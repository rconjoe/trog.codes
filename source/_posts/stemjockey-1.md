---
title: Stemjockey-1
date: 2024-07-06 08:30:41
tags: [vdj, music, demucs, linux, terminal, railway, windmill]
categories: [Stemjockey, Automation]
feature: stemjockey.png
toc: true
---

I had this idea to use something like `arecord` to programatically retain audio from some terminal-based audio thing, like `spotifyd`, and pipe it through `demucs` in the same breath, to get familiar tracks (and their stems) to practice in VirtualDJ with. To my surprise, it was much easier than I anticipated, however I was only able to obtain the desired output audio recordings using local hardware with handwritten sciripts. Trying to automate such a process on a platform like <a href="https://railway.app">Railway</a> has so far been impossible, for reasons I will get into below. 

# First attempt - local hardware

wip

# Second attempt - cloud pipelines

Using an automation platform called <a href="https://windmill.dev">Windmill</a> (which I've made a popular <a href="https://railway.app/template/UI371k">template</a> for), I was able to create pipelines that successfully utilized `ffmpeg` as a means to capture output from `spotifyd` - the latter of which requires compilation from source.

