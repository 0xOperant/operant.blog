---
title: "How to Work Asynchronously With Global Teams"
date: 2020-04-04T19:33:43-04:00
draft: true
description:
tags: ["",""]
featured_image:
copyright: false
images: [""]
author: "Dave Bell"
---
## Discussion

While we're all adjusting to the suddenly new normal of working from home, there's another challenge isn't often discussed: asynchronous remote work. The Team I'm currently with is global, including folks in the US, Europe, and Australia. Luckily for me, my teammates figured out how to tackle this long before I showed up. Once I understood the rhythms and processes, things continued to run like a well-oiled hacking machine. We're a Red Team, but there's nothing really unique about the tools or processes we use...this could work for any asynchronous team. Here's another little secret: this could work wonderfully for *any* team, even those centralized in an office. I'll try to do the techniques justice below. 

## Challenges

Working asynchronously presents an entirely new set of problems, aside from just working with remote team members. 

Time is a huge factor. If you are working with team members on the other side of the world, your working hours may not overlap. You may never be online at the same time, simply due to geography. This means you can't just ask a quick question, assuming they will completely understand the context because you are working together on a task. Quite the opposite, actually; by the time your polar opposite sees your question, they'll have no idea what the context was or whether you've already solved it yourself. This means they could waste a ton of time while just tying to help a teammate out. 

Isolation is another concern. If one person is on the opposite side of the planet from the rest of the team, that person may not get as much (online) social interaction with the rest of the team. Working remotely can be lonely enough...can you imagine not having any real-time communication with coworkers? Extra effort must be made to include teammates in this situation. 

## Context and Clarity

If your team is working asynchronously, it's probably due to necessity created by geography. When your team is distributed across the globe, culture and language differences can be barriers to effective communications, while simultaneously being a wonderful learning opportunity. This should be taken into account when considering how to ask a question of a teammate, for example. 

Don't use slang or colloquialisms, as you cannot be sure how this will be interpreted, now or later. Be clear and concise, and don't assume the reader will already know the context or background of your question. This will slow things down dramatically as clarification is sought, etc. 

Ask the question publicly, if possible. Include anyone that may have a need to know the response or be able to chime in with the answer sooner. Overshare with your teammates. Chat about what you're working on, the challenges you're facing, etc. This helps everyone understand where everyone else is  with their projects, and makes everyone feel like they're being included.

## Forgiveness vs. Permission

Not all managers can lead asynchronous teams. This is a "high trust / low control" situation, and some managers have trouble adapting to this style, especially when transitioning out of a more centralized, on-site role (characterized by "high control / low trust"). The manager must be willing to trust their people to do what they do best, and make their own decisions in real time. Mistakes will be made, sure, but these become learning opportunities for the entire team. As long as the leader provides "top cover," the team should feel comfortable making tough, time-sensitive decisions on their own and informing the leader after the fact. Trust is key. 

## Golden Rule

**Don't leave your teammates hanging.** This means everyone is doing their part to ensure that everyone else can do _their_ jobs effectively, too. If they need to make a decision in order to keep things moving, then they are expected to do so and inform the boss later (see above).

## Approach

Long form written communication is incredibly important. Everything must be documented well enough that as one person ends their day, another can begin their own, pick up the project, and run with it without skipping a beat.  The most obvious example of the use of long-form communication is [Jeff Bezos' use of "narratives" in executive meetings](https://fortune.com/2012/11/16/amazons-jeff-bezos-the-ultimate-disrupter/). If you're not familiar, these meetings start with everyone reading a printed six-page memo for up to 30 minutes.

> Bezos says the act of communal reading guarantees the group's undivided attention. Writing a memo is an even more important skill to master. "Full sentences are harder to write," he says. "They have verbs. The paragraphs have topic sentences. There is no way to write a six-page, narratively structured memo and not have clear thinking."

While this style of may seem a bit extreme, the results speak for themselves...at the time of writing Amazon's stock is $1906/share. Also note that the executives were _in the same room_. As stated previously, the benefits of long-form communication are not restricted to asynchronous or even distributed teams.

I've covered the various forms of communication that are required to work remote previously, and those same forms should be used for asynchronous teams as well. 

### * Real-time chat

For our team, this is the backbone of our communications strategy. Several team members have partially-overlapping working hours due to their geography, so they take full advantage of real-time communications. The chats are logged to a central server, which allows people to search/skim the logs to get an idea what was occurring when they come online to start their day.

Chat provides an important social connection, as well. I think we've all been part of chat channels full of gif's and memes…within professional ("Safe For Work") limits this can be quite healthy and is encouraged. Laughter is contagious and can help build morale and improve team cohesion. Meme it up!

### * Semi-ephemeral (working notes)

Over the course of collaborative asynchronous work, team members will need to generate and share working notes. Our team has been using self-hosted [Etherpad](https://etherpad.org) (only accessible via SSH tunnel) for years. It's not perfect, but it's quick and easy and it works. Etherpad may not work for your team, but the point here is that even working notes need to be collaborative, accessible, and asynchronous-capable.

### * Single Source of Truth

This is where your long-lived documentation is housed. This can be a wiki, git repo, sharepoint, whatever. Every process, system, procedure, lessons-learned, etc. should be documented in long-form and housed in this system. The assumption here is that the documents may outlast the person that originally wrote them, and so the docs must be complete and able to stand on their own without added context. Now, the documents will absolutely change over time, keeping up with reality. But this system is what will be referred to first when someone has a question, or hasn't walked through a particular process before, or is on-boarding a new hire.

### * Task / Project Management (and git)

While not every team needs a kanban, asynchronous teams definitely need a way to track projects and task progress without needing to ask someone directly for status updates. Daily stand-ups won't work here, for obvious reasons. So, team members must be diligent in creating projects, assigning tasks, and updating status as frequently as practical so that blockers can be identified and addressed quickly. If an asynchronous team is using git, small, frequent commits are encouraged along with messages that refer to up-to-date tasks. Code should not be sitting on a powered-off laptop on another continent.

### * File sharing and long term storage

While less frequent in this model, there is occasionally a need to share large files (like reports or powerpoints) that don't really belong in the wiki or a git repo. Depending on security requirements, this could be a cloud-based solution like Box, etc. Whatever this ends up being, pay attention to data classification and retention requirements so as not to inadvertently expose your company. Develop a file structure that makes sense, and stick to it so that team members can find what they need without asking someone for help.

### * Email

Email is used less frequently in an asynchronous system like this, but it does have a place. For example, a team member can use it to provide more context and rationale for some of the things they did during the day to the people that will be coming online later. This can help the oncoming team members get started without having to dig through commit messages or chat logs, and is especially appreciated if the task changed in the middle of the day, for example. Communicating the "why" helps people understand context and make better decisions.

## Tips / Recommendations
If your team is new to this, there is going to be a learning curve. The good news is that you're all learning this together, and there are some tricks you can use to smooth out those rough spots.

* If you can't be specific, be verbose
* clarify your thoughts through writing
* Never assume context or purpose is clear to all
* Be mindful of timezones when scheduling all-hands calls, reports, etc.

## fin
Working asynchronously is the next logical step after "working remotely," and will likely become more mainstream as companies embrace remote work. What are some issues you've seen working asynchronously? Comment below or on twitter!