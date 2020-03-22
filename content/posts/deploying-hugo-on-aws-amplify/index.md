---
title: "Deploying Hugo on AWS Amplify"
date: 2020-03-01T19:25:10-05:00
draft: false
description: "How to deploy Hugo on AWS Amplify"
tags: ["blog","hugo","aws","amplify","writing","how-to"]
featured_image: "aws_amplify.jpeg"
images: ["aws_amplify.jpeg"]
author: "@operant"
---
## Let's start writing (again)

Like many people, I ran a little WordPress-based blog about 13 or 14 years ago(!!). This was before social media really started, and blogging was what the cool kids were doing. And like many people, I shut it down after a few years when social media (Facebook at the time) started to take off and blogging no longer made sense. I don't remember where I hosted my blog, but I wouldn't be surprised if it was parked on one of my old homemade servers. Times have changed!

My new blogging "platform" is actually a cloud-hosted, serverless pipeline. I write my content in markdown format in a note-taking app called [Bear](https://bear.app/) (I'm typing this in Bear on my tablet right now, and I often use my phone, too!). When I'm done, I  copy and paste that content into a Hugo "new post" template on my laptop, and then commit the change to [my repository on GitHub](https://github.com/0xOperant/techblog.operant.io). AWS Amplify constantly polls that repo for changes, and automatically kicks off a complete rebuild of the blog when the new content (or changes) are detected. Once the build is complete, the blog is essentially running in a Docker container on AWS, but without all of the hassle of Elastic Container Service, and similar services. This may sound complicated, but it only takes a few minutes from pushing the git commit, to seeing the changes reflected on the live site. The Amplify console even provides screenshots of the home page (featured above) when it's done, which is pretty neat. The hardest part, by far, is finding the time to write!

Why start writing again? Three main reasons:

1. Knowledge sharing - I routinely find myself in dark corners of the internet carefully reading a blog post from the one other person who had the same crazy idea that I did, ran into some challenges, and documented the solution. I appreciate those random blog posts, and would like to share what I have learned in kind. 
2. Documentation - There have been numerous scientific studies that have shown the act of "writing" helps to clarify thoughts and increase memory retention. I've been doing a lot of crazy research and development lately, and if I don't document the solutions to the challenges I've faced, I've doomed myself to repetition. I don't have time for that!
3. Creative outlet - I'll be honest: I like it. I'm told that I write reasonably well, and I get a sense of pride and accomplishment from doing it. This is different than the feeling I get from a "job well done" at work, as this is for _*myself*_. I strongly recommend everyone find their own personal creative outlet, and deliberately make time for it. The busier you are, the more important this becomes for your health. 

Ok, but why host your own blog?

1. It's fun - I like having control over the site, and being able to do things like tweak the css, templates, or even create my own theme from scratch. I can't get that level of customization from a hosted platform. 
2. It's easier, and safer, than ever - There are several open-source frameworks available, written in pretty much every popular programming language. Find one with the features you like, and take a look at the documentation. Most of them will have instructions for deploying the framework onto various cloud platforms, which means you don't have to worry about server maintenance anymore. Pick out a theme you like, deploy the framework to your cloud of choice, and focus on your writing! You can be up and running in minutes. 
3. Medium [sucks](https://www.cdevn.com/why-medium-actually-sucks/). [That's right, it sucks](https://youtu.be/GBTR99sYBYQ)! I hesitate before clicking any links to Medium, even if I know the author and I'm interested in the subject. The user experience is just terrible, and yet Medium is the dominant hosted blogging platform. `¯\_(ツ)_/¯`

## What is Hugo

As implied by the title of this post, I chose to use the Hugo framework. [Hugo](https://gohugo.io/) is a static site generator written in go. From the site: 

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

Static websites deliver pre-generated pages directly to the browser, on request. Dynamic websites, on the other hand, require a back-end application server and database to generate content on-the-fly. Static sites sometimes purposely lack some of the features of dynamic sites, such as search and commenting, but there are themes available to re-create these functions using Javascript or other languages. I have chosen not to include these functions for security reasons and ease of maintenance. Static sites are anything but boring, however. There are themes available to suit any style and purpose, as well as easily customizable CSS templates. All of these features enable the aspiring blogger to focus on their content, and let the framework do the heavy lifting. 

## What is AWS Amplify

Until recently [AWS Amplify](https://aws.amazon.com/amplify/)  was strictly a platform for developing and hosting mobile applications. This is reflected in the market-speak on the Amplify site:

> AWS Amplify is a development platform for building secure, scalable mobile and web applications. It makes it easy for you to authenticate users, securely store data and user metadata, authorize selective access to data, integrate machine learning, analyze application metrics, and execute server-side code.

However, Amplify is now basically a condensed, easy-to-use version of an AWS CodePipeline, which means it can pull from a code repository, build the application using a `buildspec.yml` file (basically just like a Docker container on ECS), and then host the serverless application. The console even makes it easy to set up SSL/TLS certificates and manage domain names!

## Ok, let's do this

_Note: I'm assuming you already have an AWS account and an account on GitHub (or another code repository)._

First, you'll need to install Hugo. If you're running Brew on MacOS, it's just: `brew install Hugo`, and then run `Hugo new site quickStart`, and then you're already up and running! You'll want to add one of the [many free, nice-looking themes](https://themes.gohugo.io/):

```zsh
cd quickstart
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

Add the theme to your config:
`echo 'theme = "ananke"' >> config.toml`

Create your requisite "Hello World!" post:
`hugo new posts/my-first-post.md`

Fill in or modify the template header to match your needs:

```zsh
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```

Start the server (locally):

```zsh {hl_lines=[20]}
hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Now you can view your site running locally by opening `http://localhost:1313/` in your browser (from line 20, highlighted above). As you make changes to your template, content, etc., the site will automatically update so you can see your changes on the fly. This makes tweaking and testing changes much more convenient. For example, you still need to make some changes to your `config.toml`, such as update your URL, language, title, etc. You should see these changes reflected immediately. 

Once you're happy with your theme and your initial content, you'll need to push the templates to a repository that AWS Amplify can pull from (GitHub, GitLab, BitBucket, or CodeCommit as of the time of this post).  One important thing to note: because you ran `Hugo -D` prior to this step, you need delete your `Public` directory before pushing to the repo. The `Hugo -D`command generates the static pages (content) , which means later changes (commits) will have no effect. Hugo does not let you overwrite your existing content. AWS Amplify will run the command for you when it builds your site. Oh, and you can kill (ctrl+c) the locally running Hugo process, if you're done with it for now. When you want to do more testing, it's just `Hugo server` to restart it, or use `Hugo server -e production` if you want to preview what would actually get published (anything marked `draft: true` does not get generated/published).

Next, move to the [AWS Amplify console](https://console.aws.amazon.com/amplify/home) to get your pipeline running. Once you've logged in to the console, select "Get Started" and connect your git provider, repository, and branch in the drop-down menu. Whatever you select here will be monitored for changes in order to automatically trigger builds. In the next step, "Configure Build Settings", you may be able to accept the defaults, depending on your theme. I had to paste in the below settings, and added and environment variable: `HUGO_ENV = production` to get things moving properly.

```yaml
version: 0.1
frontend:
  phases:
    # IMPORTANT - Please verify your build commands
    build:
      commands:
        - wget https://github.com/gohugoio/hugo/releases/download/v0.62.2/hugo_extended_0.62.2_Linux-64bit.tar.gz
        - tar -xf hugo_extended_0.62.2_Linux-64bit.tar.gz
        - mv hugo /usr/bin/hugo 
        - rm -rf hugo_extended_0.62.2_Linux-64bit.tar.gz
        - hugo version
        - hugo
  artifacts:
    # IMPORTANT - Please verify your build output directory
    baseDirectory: public
    files:
      - '**/*'
  cache:
    paths: []
```

Once you are satisfied with you build settings, choose "Save and Deploy". Once the build process is complete (maybe a minute or two), your shiny new static site is up and running!

On initial deployment, you will be assigned a URL like `https://master.unique-id.amplifyapp.com`, but this can and should be changed in the Amplify console. In the main page above your app is a drop-down menu titled "Learn how to get the most our of Amplify Console". This menu takes you to settings pages to set up custom domain names, free SSL certificates, add password protection, set up test versions of your site, and even enable pull-request reviews. If you already have a hosted zone in AWS Route53, it takes just a few clicks to assign a domain name. SSL takes just a few minutes more.

Happy blogging! If you have any other questions or suggestions, please feel free to contact me using one of the [social platforms listed on the home page](/index.html), preferably [twitter](https://twitter.com/operant)!

## Tips

- Use `Hugo server -e production` if you want to preview what would actually get published (anything marked `draft: true` does not get generated/published).
- DO NOT push the `Public` directory to your repo. Delete it. This directory is generated by the `Hugo -D` command and contains the generated static content. Hugo will not overwrite this content, so any later changes to templates, etc. will not be reflected in the next build. AWS Amplify will generate the content as part of the build process.
- Some themes support i18n content translation better than others. If you want to support more than one language, selecting a theme with good support will save you a lot of trouble later.
- Some themes have not been updated in a few years. Hugo has changed, so look for more actively-maintained themes.
- Speaking of themes, get familiar with `git submodule deinit`, which will help you remove old/broken themes (submodules).
- As you experiment with themes, copy the whole site to another directory, then apply the new theme. Don't experiment in the directory where your current, live site resides.
- [Hugo Shortcodes](https://gohugo.io/content-management/shortcodes/) make it easy to add images or pull in content from social media.
- Block off time on your calendar to write, and enable a reminder. Otherwise this is all for naught.

## References

I pulled heavily from the official docs, as they worked quite well for me:

- [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/)
- [Host on AWS Amplify](https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/)
