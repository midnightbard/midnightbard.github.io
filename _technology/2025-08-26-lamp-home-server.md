---
layout: technology
media: journal
description: A few stuff about home server, intranet and social media scheduler 
comments: true
image: https://i.imgur.com/JfaKi81.png
title: LAMP home server and other things
date: 2025-08-26
---

I revamped a discarded PC and installed LAMP on it. It is a home server, which means no hosting online due to the nature of my connection ( mobile) but I can build it into anything for personal use.  

> A LAMP server is a popular open-source web development platform that combines four key components: **L**inux, **A**pache, **M**ySQL, and **P**HP. It provides a complete and reliable environment for hosting websites and web applications. The four components work together to deliver web content: Linux as the operating system, Apache as the web server, MySQL for database management, and PHP for server-side scripting.

Years ago I worked on WordPress so I installed that and Piwigo. Personally I think WordPress is enough due to extensive plugins and options. 

The only thing it missed, to be an absolute solution for my in-house tool for me and my team - is a social media post scheduler. All available tools were either paid or limited, and most of them don't have all networks I am interested to include into our project. 

So, I built that part on my own, and for now it schedules posts for Bluesky, Mastodon, Threads, Tumblr and Discord. 

The hardest part to make was Threads; Meta programming ( Facebook ) significantly changed from the time I was working on it. 

Anyways I created a working program for other four in a day, and the next day I needed to learn and figure out how Threads suppose to work. 

I needed an extra day to polish a front end design, adjust it to mobile template, and to install additional scripts for extra features - buttons, calendar, draft posts and some quirks etc etc. 

Today the whole thing had a fall-out because of the unstable network conditions and glitches due to - I guess - solar flares. They reported we had five in a row and that it MIGHT disrupt some things. 

That was a great opportunity to install additional safety measurements, so that cron doesn't fall out of a key, and all of it works smoothly and without glitches. 

Glitches will happen , because this is a server side website and Rune ( my neighbour who is a social media manager) is using it on a home connection.

Yes, I established a sort of a intranet, and yes my team already asked if it can host games and other, more profound tools, like 3D modelling...

Rune used to work with Buffer and he was used to have a database of drafts, so I built an additional page for that as well, with search, colour coded networks, edits ... etc...

Buffer also has a calendar view, so I made an extra widget with that too. 

Anyways, an app is very simple and this is how it looks like ( for now): 



#### Dashboard 

<img src="https://i.imgur.com/JfaKi81.png" class="img-thumbnail"/>

#### New post scheduler

<img src="https://i.imgur.com/HD43SKg.png" class="img-thumbnail"/>


#### Calendar view

<img src="https://i.imgur.com/Z8KhJuR.png" class="img-thumbnail"/>

#### Drafts 

<img src="https://i.imgur.com/FFFPbup.png" class="img-thumbnail"/>

<img src="https://i.imgur.com/t4hSBtc.png" class="img-thumbnail"/>

***

I will make sure that all this works smoothly, and then additionally probably some time next month I will upgrade it for TikTok and Pinterest. 

***
