---
title: "How to Sound Like a Podcaster on Your Next Call"
date: 2020-03-15T18:58:19-04:00
draft: false
description: "audio quality can make or break a call, video, or stream"
tags: ["home-office","how-to","skype","streaming","remote-work"]
featured_image: "/images/microphone.jpg"
images: ["/images/microphone.jpg"]
author: "Dave Bell"
---
I covered video in a previous post [(Chroma Keying for Skype in MacOS)](../chroma-keying-for-skype-on-macos/), so I thought I would follow that up with a post on audio. Audio quality can make, or break, any call, video, or stream. Think about the last time you tried to watch an interesting looking video on Youtube, only to turn it off due to horrible sound. Or the last time you had a call where you wondered if that one person (you know the one) was actually drowning. Or the mouth-breather. The list goes on...you don't want to be on that list, do you? I thought not. Let's get your audio sorted.

## Hardware

We need to start with a few essentials. First and foremost: your microphone. I know you have some fancy bluetooth earbuds, or cans, or whatever, and your music sounds amazing. Those are made for audio _output_, not _input_. Everyone else thinks you sound like crap, trust me. Those earbuds have omnidirectional microphones that pick up absolutely everything going on around you at the same volume as your voice, especially if you're a "[low talker](https://youtu.be/vKWYg9qFOpA)". Don't worry, though, we can probably still salvage your current headphones.

If this is your first actual microphone, I'd recommend sticking with USB. It's cheaper, and for what we're doing, more than adequate. Don't get sucked into buying an XLR microphone that requires an external mixer, etc. The irony is that most mixers are USB anyway, and we can do a lot of what a mixer does with software (below). For USB microphones, I recommend [Yeti](https://www.bluedesigns.com/products/yeti/) microphones from Blue Designs. I have a Yeti and a Yeti Nano, and they've both been great so far...at least compared to my old speakerphone. I do get compliments and questions regarding my setup regularly, so I must be doing something right! I also recommend mounting the microphone on an arm with a shock-mount. I do NOT recommend the Blue Compass, which is included with the "Yeticaster" kit in the center of the below picture. It looks cool, but it's not meant to be folded up/rotated out of the way frequently. I broke two of them, and I'm pretty careful with my gear. I ended up going with this arm from [Neewer](https://www.amazon.com/dp/B07T44VVGF?ref=ppx_pop_mob_ap_share) and have been pretty happy with it. The [Yeti Radius III](https://www.bluedesigns.com/accessories/) suspension mount has been great so far.

![Blue Yeti Microphones](/images/yeti.png)

Why do we need an arm and shock mount? These microphones are sensitive, and will pick up every bump and vibration. If you leave the mic on a stand on your desk next to your keyboard, you definitely will bump and rattle it more often than you might imagine. An arm also allows you to get the mic up closer to your mouth, so you can lower the gain (sensitivity) and hopefully not pick up so much extraneous noise. Your callers/viewers will appreciate that!

If you mount the arm on the back edge of your desk like I did, a 6ft (~1.5m) audio extension cable will come in handy. Many USB microphones have a 3.5mm audio jack, allowing you to plug in a headset to "monitor" your raw input. You hear exactly what the mic hears, so you can adjust the gain, fix rattles and squeaks, etc. I ran this under my desk, and back up to the front edge for convenience. I also use a pair of [Shure SE-215s](https://www.shure.com/en-US/products/earphones/se215) (plugged into the extension cable) for my audio during calls. They are clear, and the cables route back over the top of my ears and down my back. They're pretty much invisible, sound great, and I don't notice the cable for the most part. I was worried about being "tethered to the desk," but I'm on a video call anyway...where am I going to go? One other thing about the Shure monitors: they are noise _isolating_, not noise _cancelling_, so they are not adding hiss to your audio. This is important when you're monitoring your microphone and trying to determine what your listeners will actually hear. The Shure's block out sound quite well with the included ear tips, but they also sell a variety of fancier tips, including triple-flange and even foam to help block out ALL the noise. They're essentially ear-plugs with great speakers in them! I went the extra mile and bought the clear cable to go with them, so there's no black cable arching over the top of my ears. Just personal preference, and the cable is ~$25.

![Shure SE-215](/images/shure.png)

One final item on our list: a pop filter. These are commonly referred to as "spit shields," which isn't entirely wrong. What they do is protect the microphone's sensitive internals from "plosives." A plosive is the puff of air that expels from your mouth when you, for example, pronounce the word "plosive," or any other word that start with a "T" or "P." Hold your hand up to your mouth and say "peter picked a peck of pickled peppers." See? There are two kinds of pop filters: the foam sock that fits over the top of the microphone, or the shield that is mounted on a flexible arm and positioned between the mouth and the microphone. Either will work, but this will be a "personal preference" thing. You'll end up trying a few until you find what you like, and don't like. I finally settled on a [Stedman PS101](https://www.stedmanusa.com/pop-filters) pop filter.

### Hardware shopping list

* USB Microphone
* Microphone arm
* Suspension Mount
* 3.5mm audio extension cable (optional)
* hardwired audio monitors (optional, but recommended)
* pop filer

## Software

After some trial and error, I ended up using [Apple's Mainstage 3](https://apps.apple.com/ca/app/mainstage-3/id634159523) to clean up my audio before broadcasting. It's definitely overkill, but the interface is pretty easy to use and I was able to get started pretty quickly with just a few tweaks. There are open source alternatives, however, such as Reaper and OBS. Reaper is a full-featured Digial Audio Workstation (DAW), while Open Broadcast Studio (OBS) is geared more towards video. Either choice will allow you to do the important things we need, like noise gating and compression, explained below.

Of course, you have to get Mainstage's output into the right input, somehow. For example, skype / teams doesn't have an option to select another application as the audio input; you have to select what it thinks is a hardware device. To solve this issue, I chose [Loopback from RogueAmoeba](https://rogueamoeba.com/loopback/). I've since learned it's possible to use Apple's built-in Audio Midi Setup app to do this, but I think Loopback's interface is much more user-friendly.

The Blue Sherpa companion app for the Yeti microphones is also useful, as it allows you to adjust the gain and even mute the direct monitoring feature if desired. It also provides a way to update firmware, etc. It's not necessary, but useful.

### Software shopping list

* Digital Audio Workstation
* Loopback / audio routing app
* Mic companion app

## Putting it all together

Ok, now for the fun part. You have your shiny new microphone mounted and connected, you've installed your DAW, and you're ready to get started. I'm going to assume you stuck with my recommendations, and are using Mainstage 3. Go ahead and launch Mainstage, and you'll be greeted with a menu:

![Mainstage Wizard](/images/mainstage_wizard.png)

On the left, choose "Vocals." Mainstage should now be open full-screen, which drives me crazy. In any case, we're going to make some changes here. First, let's check our audio input preferences. Press `cmd+,` to open the preferences pane, and make sure you have the correct settings for your equipment in the "Audio" tab. The Blue Yeti has a sample rate of 44.1kHz, 16-Bit (make sure 24-Bit is unchecked). The Yeti Nano _does_ record in 24-bit, so check your mic and make the appropriate adjustments, if needed. You will have bizarre problems if these settings don't match your gear.

![Mainstage Preferences](/images/preferences.png)

To the right of the mainstage console, you should see some "Channel Strips":

![Channel Strips](/images/mainstage_channels.png)

We need to tweak these. The left-most channel strip is the "Natural Voice" strip (labels are at the bottom). We need to add two "Audio FX" settings, so click at the bottom of the blue stack in that channel to add the Noise Gate FX:

![Noise Gate](/images/mainstage_gate.png)

By using a [Noise Gate](https://en.wikipedia.org/wiki/Noise_gate), we are setting a threshold for when we want the microphone to activate, and deactivate. We only want the mic to activate for our voices, and (hopefully) ignore anything else. Because the mic is positioned near out mouths (right?), we can set the threshold fairly high. Before that threshold is reached, the mic is basically off, resulting in dead silence. Don't be surprised if someone asks if you're still on the line! You're going to have to play with your settings a bit to account for your own equipment and environment, but I've included mine below. Be sure to drag the noise gate to the top of the stack, so it is processed first.

![Noise Gate Settings](/images/noisegate_settings.png)

Next repeat the process, but choose "[Expander](https://recordmixandmaster.com/2010-06-what-is-an-expander)," also from the Dynamics menu. This FX will basically increase the dynamic range of your voice, giving it that "broadcaster" sound. Move this to the bottom of the stack. Again, you'll need to play with your settings to get things sounding the way you like, but I've included a screenshot of my settings below.

![Expander Settings](/images/expander.png)

Your channel strip should now look like the below, with the noise gate at the top of the FX list, and the expander at the bottom.

![New Channel Strip Settings](/images/finalchannelstrip.png)

Ok, we're done with mainstage. I recommend saving this "concert" so you can quickly open it before a call, and be ready to go. Next, we need to configure Loopback. Luckily, this is pretty much a point-and-click affair, as you can see below. On the left are the "input sources," which are applications like mainstage and music. In the middle are "channels" that you use to route the signal, and on the right are "monitors" which you use to listen to the output. Don't let the fact that there are microphones in the monitor section confuse you...recall that these mic's have 3.5mm audio jacks specifically for monitoring. The thing to remember is that the audio signal flows from left to right. You'll need to add mainstage as a source on the left, and then click-and-drag the (L) and (R) outputs to the (L) and (R) inputs in "Channels 1 & 2." Then add your monitoring device, and repeat the click-and-drag. That's it! You'll notice I have a second source (Music) piped into Channels 1 & 2, as well. This means that I can do things like play background music at a low volume while waiting for everyone else to join the call. You're only limited by your imagination! Have some fun with it. This page has some other [cool things you can do with Loopback](https://rogueamoeba.com/support/knowledgebase/?showArticle=LB2HiddenSources).

![Loopback](/images/loopback.png)

That's it! If all went well, you should be sounding like a professional and be the envy of your conference call! Now pair this with a [green screen](./chroma-keying-for-skype-on-macos/), and you'll look like a professional broadcaster. {{< emoji ":wink:" >}}

## Tips / Recommendations

You'll want to test your sound before going "live" or making a call. I suggest using GarageBand to practice with. Record yourself speaking naturally, and then listen to it. Play with your settings adjust your gain and volume, turn desk fans on/off, tap on the keyboard, etc. Figure what is going to make unwanted noise, then tweak, test, and repeat. Once you're comfortable with everything you can start integrating your new setup into your calls. But don't do it before you're ready...there are a lot of settings here, and if something goes weird during a call, it will be tough to troubleshoot live while people are waiting. If you're rocking a green screen, make a video! You'd be surprised what you can learn from a couple of minutes of watching and listening to yourself. I know I did! I also recommend taking a look at the [mainstage documentation](https://support.apple.com/mainstage). Bookmark it, too, because when you begin to test and tweak your settings, you'll want to refer to the docs to understand why things are acting the way they are. When I wanted to test something, I would create a new concert so I wouldn't mess up my old settings, too.

## fin

Ok, at this point, you should be ready to start playing with your new setup. Let me know how it goes! If you need help, feel free to comment below or ping me on [twitter](/images/https://twitter.com/operant); I leave my DMs open.
