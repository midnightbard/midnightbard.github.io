---
layout: technology
media: journal
title: YouTube streaming from home server
description: A few words about broadcast, a prerecorded live stream for YouTube
comments: true
image: https://i.imgur.com/Sic4yV7.png
date: 2025-09-09
---

There is more than one reason why I wanted a home server, and it is not only for team organization and social media scheduler - which also turned out to be great to have. 

With home server I can stream my content - it is not a live stream, better word would be a broadcast. 

A script is very simple and needs only a few tweaks on YouTube; well, so far what I managed to put together for a simple purpose of advertising my tarot service. So, that is for a start. Later I will use it for more than just that one thing. 

I tried with video premiere with chat, but it didn't get much of a traction, so I opted for a full fledged stream solution. 

First, a video. 

I created a video that will serve as an info for my service, it is very short, a few minutes, a few static images for decoration at the end of a video. 

Then I shrink it with a Handbrake and uploaded into a video folder on my server. 

Second, a script with cron job. 

Script defines what is happening with a video and cron when it will run. I decided to loop my video and to start running it late at night when I am usually already sleeping. 

Third, YouTube settings. 

My script needs link, key and settings for auto start and stop in my live stream Studio to be on. 

So broadcast will be started by a timer in cron, and once a loop is done, a live broadcast will shut down. 

*** 

Future plan is to produce list of small videos and to create a whole night entertaining program and then run it on days I find appropriate. 

Live streams that have chat available for customers will be moderated by Penny, as all this is happening inside of her time zone while I sleep. 

*** 




