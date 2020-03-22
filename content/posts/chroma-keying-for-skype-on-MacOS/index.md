---
title: "Chroma Keying for Skype on MacOS"
date: 2020-02-23T19:14:48-05:00
draft: false
description: "How and why I use a chroma key (green screen) in Skype for Business calls"
tags: ["skype","streaming","how-to","chroma key","MacOS","green screen","wirecast","obs","ecamm live"]
featured_image: "/chroma-keying-for-skype-on-MacOS/greenscreen.jpeg"
images: ["/chroma-keying-for-skype-on-MacOS/greenscreen.jpeg"]
author: "@operant"
---
{{< copyright >}}

## Chroma what?

I've been using a "green screen" [(chroma key)](https://en.wikipedia.org/wiki/Chroma_key) in my Skype for Business calls for a few months now, and I'm frequently asked how I set it up. This post will give you a rough idea of why I'm using a green screen, and how to set up your own if you so choose. Here's an idea what the end result looks like:

{{< twitter 1237797696410353669 >}}  

## Why?

I've been working remotely for almost five years now, and most of that time has been spent leading a team spread across the globe.  In this time, I've discovered that turning on the webcam during conference calls has several benefits:

1. Clarity of communication: Just as real-time voice allows greater "bandwidth" when communicating (vs. text-based chat, for example), being able to see one another's facial expressions dramatically increases everyone's understanding of what is being said. This is especially important when there are differences in languages or cultures.

2. Self-Discipline: Working remotely creates powerful temptations to develop terrible habits. If nobody can see you, who's to know that you literally just rolled out of bed and dialed into the conference call...right? Just knowing that you will spend time live on camera today helps to develop and reinforce healthy habits, such as waking up at a regular time, eating, showering, and dressing for work like a normal person. This also _may_ make it more likely that you will actually leave your house on a given day, which is another hazard of pure remote work (look out for a full post on remote work soon).

3. Trust: I spend quite a bit of time on calls with executives, and I'm usually not bringing them good news (I lead our internal Red Team). Showing my face builds trust, as I'm no longer just some random voice on a speakerphone trying to ruin someone's weekend. Careful use of facial expressions coupled with a light-hearted comment can also help de-escalate any rising tensions.

4. It's fun! I pick out new backdrops regularly, and it's a great icebreaker when first joining a call. I normally get a few comments every time, frequently followed up with requests for a tutorial. If I'm comfortable with the attendees, I sometimes use funny backdrops that make it look like I'm in a padded cell or something like that...I'm only limited by my creativity (and the message I want to send). If I'm going to be on camera, I'm going to have fun with it!

Now, _all of the above can be accomplished without a green screen_. A simple backdrop will work fine, if like me you just want to block out a distracting background.  That is actually how I started down this path…a simple photographer's backdrop that made it look like I was sitting against the wall of a barn or something (large horizontal rustic wooden boards). It was my daughter that suggested I get a green screen instead, and unknowingly created a monster!

## Requirements

To get chroma keying working with Skype for Business, you will need a few things, which I have listed below. Skype does not natively support chroma key effects, so you will need to configure it to use a "virtual webcam" as the camera source.  Skype treats the virtual webcam just like any other USB webcam, so we have to insert the chroma key effect _before_ the picture/signal gets to Skype. I tried three different software platforms before settling on Wirecast One, but your needs and budget may vary. Important note about OBS: it no longer supports process injection on MacOS. Security features in Mojave and Catalina prevent OBS from capturing the image via Syphon Inject / CamTwist. This means that you will need to purchase a license for Wirecast or eCamm Live for this to work on anything newer than High Sierra.

### Hardware

1. Green Screen (~$14 on Amazon)
2. Frame for screen (~$35 on Amazon)
3. Extra clips for mounting the screen to the frame (optional) (~$10 on Amazon)
4. Lighting  (cost varies dramatically)

A word about lighting: this is critical, but it doesn't have to break the bank. You need a couple of lights that put out the right color temperature (5600K) and are bright enough to eliminate shadows on the backdrop. My desk is against a window, so I am just using a pair of these on my desk: [Neewer Dimmable 5600K USB LED Video Light with Adjustable Tripod Stand](https://www.amazon.com/gp/product/B07T8FBZC2/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1). Set these above and off to either side of your face, and experiment with the brightness settings until you get a soft, natural looking effect.

### Software

* Virtual Camera output options:

  * [Live Video Streaming Software | Wirecast](https://www.telestream.net/wirecast/) - paid, ecommended
  * [Open Broadcaster Software | OBS](https://obsproject.com/) - free, doesn't work on Mojave or Catalina
  * [Ecamm Live - Powerful Live Streaming Platform for Mac - Ecamm Network](https://www.ecamm.com/mac/ecammlive/) - cheaper, less features

* Backdrops!

    I try to find backdrops that are interesting/cool looking, are high resolution, and are not distracting. I want my audience to be impressed, but still listen to what I have to say. Skype for Business can only broadcast at 720p, so be sure to look for backdrops that will look good at that resolution (or better). Good animated backdrops will likely cost a bit of money, but there are plenty of free still shots available on the web. The below sources should get you started:

  * [Creative Commons](https://search.creativecommons.org) - free
  * [Flickr Creative Commons](https://www.flickr.com/creativecommons/) - free
  * [Shutterstock](https://www.shutterstock.com/home) - paid
  * [Adobe Stock](https://stock.adobe.com) - paid


## Configuration

There are a number of excellent tutorials and video walk-throughs available already, so I will link to them here. If you have issues or questions, please feel free to contact me using one of the [social platforms listed on the home page](../../index.html), preferably [twitter](https://twitter.com/operant)!

Wirecast:

* [How to Set up ChromaKey in Wirecast - YouTube](https://www.youtube.com/watch?v=FTe_7Gq_l5o)
* [How to use chroma key with a greenscreen in Wirecast](https://streamshark.io/wirecast-guide/chroma-key)

OBS:

* [How To Use Chroma Key Software For Live Streaming - OBS Chroma Key Guide - Green Screen Live Stream](https://streamshark.io/blog/chroma-key-software-live-streaming/)

eCamm Live:

* [Ecamm Live: How To Use A Green Screen - YouTube](https://www.youtube.com/watch?v=6G4ZOAdgmPU)

## Practical use considerations / tips

As mentioned above, lighting is critical. If you're not getting the results you want, try playing with the lighting first. The software can only fix so much. Moving the screen forward (mine is right behind my chair) can solve a lot of problems too. One other tip is that you don't necessarily a huge 10'x10' backdrop. If your software supports cropping and zooming, you can get away with a much smaller backdrop…depending on the lighting! The trick is to use layers in your "shot," so the layer you are in is cropped and zoomed, but the layer with the background (replacing the green screen) is scaled to fit.
