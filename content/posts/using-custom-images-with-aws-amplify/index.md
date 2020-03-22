---
title: "Using Custom Images With AWS Amplify"
date: 2020-03-10T21:06:58-04:00
draft: false
description: "don't use the bloated default image!"
tags: ["hugo","docker","aws","amplify","iam","ecr"]
featured_image: "/using-custom-images-with-aws-amplify/hugo-docker-aws.png"
images: ["/using-custom-images-with-aws-amplify/hugo-docker-aws.png"]
author: "@operant"
---
## Bloated Whale

One thing that I love about Hugo, is that it's a self-contained go binary. This means it's really easy to run a local version of my site temporarily as I'm writing content or tweaking the design. I was doing just that the other evening, when I noticed that one page didn't look the same locally as it did "live." Investigating this, I noticed that I was running a different version locally than I was on AWS. As I was looking at the logs, however, something else jumped out at me: the default docker image on AWS Amplify is _bloated_. It's like they tried to anticipate every possible use case, and cram all of the dependencies into one default image. I saw three versions of Node, two versions of Ruby, Hugo, Jekyll, Cypress...the list goes on. This defeated the whole point of wanting to use a docker image: a nice, clean, minimal image with only the absolute necessities running. AWS Amplify supports using custom images, so that's what I set out to build.

Default AWS Amplify Dockerfile Monstrosity:

```bash
# Use the standard Amazon Linux base, provided by ECR/KaOS
# It points to the standard shared Amazon Linux image, with a versioned tag.
FROM 137112412989.dkr.ecr.us-west-2.amazonaws.com/amazonlinux:2
MAINTAINER Amazon AWS

# Framework Versions
ENV VERSION_NODE_8=8.12.0
ENV VERSION_NODE_10=10.16.0
ENV VERSION_NODE_12=12
ENV VERSION_NODE_DEFAULT=$VERSION_NODE_10
ENV VERSION_RUBY_2_4=2.4.6
ENV VERSION_RUBY_2_6=2.6.3
ENV VERSION_BUNDLER=2.0.1
ENV VERSION_RUBY_DEFAULT=$VERSION_RUBY_2_4
ENV VERSION_HUGO=0.55.6
ENV VERSION_YARN=1.16.0
ENV VERSION_AMPLIFY=1.12.0

# UTF-8 Environment
ENV LANGUAGE en_US:en
ENV LANG=en_US.UTF-8
ENV LC_ALL en_US.UTF-8

## Install OS packages
RUN touch ~/.bashrc
RUN yum -y update && \
    yum -y install \
        alsa-lib-devel \
        autoconf \
        automake \
        bzip2 \
        bison \
        bzr \
        cmake \
        expect \
        fontconfig \
        git \
        gcc-c++ \
        GConf2-devel \
        gtk2-devel \
        gtk3-devel \
        libnotify-devel \
        libpng \
        libpng-devel \
        libffi-devel \
        libtool \
        libX11 \
        libXext \
        libxml2 \
        libxml2-devel \
        libXScrnSaver \
        libxslt \
        libxslt-devel \
        libyaml \
        libyaml-devel \
        nss-devel \
        openssl-devel \
        openssh-clients \
        patch \
        procps \
        python3 \
        python3-devel \
        readline-devel \
        sqlite-devel \
        tar \
        tree \
        unzip \
        wget \
        which \
        xorg-x11-server-Xvfb \
        zip \
        zlib \
        zlib-devel \
    yum clean all && \
    rm -rf /var/cache/yum

## Install Node 8 & 10 & 12
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
RUN curl -o- -L https://yarnpkg.com/install.sh > /usr/local/bin/yarn-install.sh
RUN /bin/bash -c ". ~/.nvm/nvm.sh && \
    nvm install $VERSION_NODE_8 && nvm use $VERSION_NODE_8 && \
    nvm install $VERSION_NODE_10 && nvm use $VERSION_NODE_10 && \
    npm install -g sm grunt-cli bower vuepress gatsby-cli && \
    bash /usr/local/bin/yarn-install.sh --version $VERSION_YARN && \
    nvm install $VERSION_NODE_12 && nvm use $VERSION_NODE_12 && \
    npm install -g sm grunt-cli bower vuepress gatsby-cli && \
    bash /usr/local/bin/yarn-install.sh --version $VERSION_YARN && \
    nvm alias default node && nvm cache clear"

## Install Ruby 2.4.x and 2.6.x
RUN gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB && \
    curl -sL https://get.rvm.io | bash -s -- --with-gems="bundler"

ENV PATH /usr/local/rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
RUN /bin/bash --login -c "\
    rvm install $VERSION_RUBY_2_4 && rvm use $VERSION_RUBY_2_4 && gem install bundler -v $VERSION_BUNDLER && gem install jekyll && \
    rvm install $VERSION_RUBY_2_6 && rvm use $VERSION_RUBY_2_6 && gem install bundler -v $VERSION_BUNDLER && gem install jekyll && \
    rvm cleanup all"

## Install awscli
RUN /bin/bash -c "pip3 install awscli && rm -rf /var/cache/apk/*"

## Install SAM CLI
RUN /bin/bash -c "pip3 install aws-sam-cli"

## Install Hugo
RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION_HUGO}/hugo_${VERSION_HUGO}_Linux-64bit.tar.gz && \
    tar -xf hugo_${VERSION_HUGO}_Linux-64bit.tar.gz hugo -C / && \
    mv /hugo /usr/bin/hugo && \
    rm -rf hugo_${VERSION_HUGO}_Linux-64bit.tar.gz

## Installing Cypress
RUN /bin/bash -c ". ~/.nvm/nvm.sh && \
    nvm use ${VERSION_NODE_DEFAULT} && \
    npm install -g --unsafe-perm=true --allow-root cypress"

## Install AWS Amplify CLI for VERSION_NODE_DEFAULT and VERSION_NODE_10
RUN /bin/bash -c ". ~/.nvm/nvm.sh && nvm use ${VERSION_NODE_DEFAULT} && \
    npm install -g @aws-amplify/cli@${VERSION_AMPLIFY}"
RUN /bin/bash -c ". ~/.nvm/nvm.sh && nvm use ${VERSION_NODE_10} && \
    npm install -g @aws-amplify/cli@${VERSION_AMPLIFY}"

## Environment Setup
RUN echo export PATH="\
/usr/local/rvm/gems/ruby-${VERSION_RUBY_DEFAULT}/bin:\
/usr/local/rvm/gems/ruby-${VERSION_RUBY_DEFAULT}@global/bin:\
/usr/local/rvm/rubies/ruby-${VERSION_RUBY_DEFAULT}/bin:\
/usr/local/rvm/bin:\
/root/.yarn/bin:\
/root/.config/yarn/global/node_modules/.bin:\
/root/.nvm/versions/node/${VERSION_NODE_DEFAULT}/bin:\
$(python3 -m site --user-base)/bin:\
$PATH" >> ~/.bashrc && \
    echo export GEM_PATH="/usr/local/rvm/gems/ruby-${VERSION_RUBY_DEFAULT}" >> ~/.bashrc && \
    echo "nvm use ${VERSION_NODE_DEFAULT} 1> /dev/null" >> ~/.bashrc

ENTRYPOINT [ "bash", "-c" ]
```

## Which Diet

Ok, so we need to slim down the Dockerfile. When I think "small", I think Alpine. So I quickly pulled together an alpine dockerfile with the bare essentials. Note that my theme requires Hugo_Extended; you may not need this version.

Working Alpine + Hugo Dockerfile:

```bash
FROM alpine:3.11

ENV VERSION_HUGO 0.67.0

# Install dependencies
RUN apk add --no-cache git openssl openssh py-pygments libc6-compat g++ curl

## Install Hugo
RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION_HUGO}/hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz && \
    tar -xf hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz hugo -C / && \
    mv /hugo /usr/bin/hugo && \
    rm -rf hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz

EXPOSE 1313
ENTRYPOINT [ "sh", "-c" ]
```

This worked great, locally. I cloned my site, launched hugo, and everything looked good. So I quickly set about pushing the image to AWS Elastic Container Repository (ECR), because I'm already using Amplify anyway. So I followed the instructions, pushed the container image to ECR, and triggered a new build...which promptly failed. Amplify didn't have permissions to pull from ECR. I was tired, and didn't want to deal with IAM, so I just pushed the image to Docker Hub instead (which Amplify supports). At this point I pointed Amplify at the docker registry, and triggered another build. But, nothing happened. The Amplify documentation specifically says to use the normal docker syntax, and gives an example of `docker pull image:tag`. Only that doesn't work. You have to omit the tag for Amplify to "find" the image. After solving that mystery, I triggered yet another build. This one provisioned successfully! But the build silently failed. No logs, no alerts; nothing but a big red {{< emoji ":x:" >}}. I tweaked various settings, tried adding the AWS CLI, etc., until I found [this post](https://github.com/aws-amplify/amplify-console/issues/100#issuecomment-528598420) stating Alpine isn't supported by Amplify. Awesome. {{< emoji ":unamused:" >}}

I was tempted to try ubuntu next. I'm familiar with it, and can get the image pretty small. However, I didn't feel like playing "whack a mole" anymore, especially with such sparse and often incorrect documentation on Amazon's part. No, instead I just cut out the important bits from their default dockerfile, and stuck with Amazon Linux 2. I'm pretty sure they'll support that! {{< emoji ":stuck_out_tongue:" >}} Here's what I ended up with after trimming the blubber. This works locally, and on AWS. Once again, I'm using the extended version for my theme. Amplify will ignore the `EXPOSE` command, so I just left it in there for when I want to pull the image for local testing.

Slimmed-down version of the default dockerfile:

```bash
FROM amazonlinux:2

ENV VERSION_HUGO=0.67.0

RUN yum -y update       && \
    yum -y install         \
        git                \
        openssl            \
        openssh-clients    \
        py-pygments        \
        libc6-compat       \
        g++                \
        curl               \
        wget               \
        tar                \
    yum clean all       && \
    rm -rf /var/cache/yum

## Install Hugo
RUN wget https://github.com/gohugoio/hugo/releases/download/v${VERSION_HUGO}/hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz && \
    tar -xf hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz hugo -C / && \
    mv /hugo /usr/bin/hugo && \
    rm -rf hugo_extended_${VERSION_HUGO}_Linux-64bit.tar.gz

EXPOSE 1313
ENTRYPOINT [ "bash", "-c" ]
```

We went from 137 lines down to 26, and it could definitely be shorter if I didn't care about readability. I built the image locally, attached to the shell, cloned my site from github, and then launched hugo. It worked like a charm, and now my locally generated page matched the live page. Cool! Now the only thing I needed to do was to push the image. Right?

At this point I planned to continue to use docker hub, as I still did not want to mess with IAM permissions. I pointed docker hub at the github repo for the dockerfile, then set up a webhook to trigger Amplify to redeploy whenever a new image was built on docker hub. Then, I triggered the build pipeline by pushing the dockerfile to github. And waited. And...waited some more. Docker Hub seems really slow to me. However, it eventually did it's thing, and dutifully notified Amplify that there was work to do. Amplify dove on that grenade immediately, and deployed a fresh version of my site in no time at all. I brought up a browser to double check, and everything looked good. Sweet! But I had been spoiled. Docker hub was just too slow, and I didn't want to wait for it while I was tweaking content or cosmetics. I knew I would get frustrated with that quickly. What to do?

I could have just built the image locally, and then pushed it...but that option kind of sucked too. I'd been spoiled by triggering things by pushing git commits. I knew that ECR would be much faster, and it made sense to keep the dockerfile on AWS. So, I found myself fighting with IAM.

Amplify needed read access to the ECR image repository in order to be able to pull the image and start the build. In order to provide that access, I first created an IAM role for the Amplify service to assume, and then created a read-only policy document in the ECR console and assigned it to the role:

```json
{
  "Version": "2008-10-17",
  "Statement": [
    {
      "Sid": "AmplifyReadHugo",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<accountID>:role/AmplifyAssumeRole",
        "Service": "amplify.amazonaws.com"
      },
      "Action": [
        "ecr:BatchCheckLayerAvailability",
        "ecr:BatchGetImage",
        "ecr:DescribeImageScanFindings",
        "ecr:DescribeImages",
        "ecr:DescribeRepositories",
        "ecr:GetAuthorizationToken",
        "ecr:GetDownloadUrlForLayer",
        "ecr:GetLifecyclePolicy",
        "ecr:GetLifecyclePolicyPreview",
        "ecr:GetRepositoryPolicy",
        "ecr:ListImages",
        "ecr:ListTagsForResource"
      ]
    }
  ]
}
```

Once that was done, I headed back to the Amplify console, clicked "Redeploy this Version", and watched the magic happen.

## fin

I'm pretty happy with the results. The new dockerfile is tiny compared to the default, and I've removed a ton of useless code from the image, thereby reducing possible risk. Amplify was already pretty snappy, but this does seem to be a bit faster, which is nice. The dockerfile is available on my [github](https://github.com/0xOperant/hugo-amazon-docker/blob/master/Dockerfile), if you'd like to try it. The image is also on [Docker Hub](https://hub.docker.com/r/operant/hugo) (`docker pull operant/hugo`), if you're into running other people's containers. It works locally, too...you don't need to run it on AWS. [Let me know](https://twitter.com/operant) how it works for you!
