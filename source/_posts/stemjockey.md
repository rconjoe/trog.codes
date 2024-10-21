---
title: Stemjockey
date: 2024-07-06 08:30:41
tags: [vdj, music, demucs, linux, terminal, railway, windmill]
categories: [Automation, DeadProjects]
feature: stemjockey.png
---

I had this idea to use something like `arecord` to programatically retain audio from some terminal-based audio thing, like `spotifyd`, and pipe it through `demucs` in the same breath, to get familiar tracks (and their stems) to practice in VirtualDJ with. To my surprise, it was much easier than I anticipated, however I was only able to obtain the desired output audio recordings using local hardware with handwritten sciripts. Trying to automate such a process on a platform like <a href="https://railway.app">Railway</a> has so far been impossible, for reasons I will get into below. 

# First attempt - local hardware

I was able to get a semblance of this working on a Raspberry Pi Compute Module 4. `arecord` records the output of `spotifyd`, while a python script calls the Spotify API to get the song metadata, which is then stored alongside the resulting .wav file.

Bash scripts are then used to create necessary file structures and run the .wav through the command-line `demucs` utility, for however many sources I want, renaming the output files appropriately.

Furthermore, since `spotifyd` shows up as a device on Spotify Connect, I am able to trigger this entire process by playing Spotify from my phone and choosing the Pi as my playback device. Way more luxurious than I anticipated.

# Second attempt - cloud pipelines

Using an automation platform called <a href="https://windmill.dev">Windmill</a> (which I've made a popular <a href="https://railway.app/template/UI371k">template</a> for), I was able to create pipelines that successfully utilized `ffmpeg` as a means to capture output from `spotifyd` - the latter of which requires compilation from source. I was able to compile all the required software and supply Railway with a Docker image with the required binaries. However, I found that audio was either missing or, due to access restrictions on machines from VPS providers, inaccessible to the end user. I couldn't find any audio devices using `aplay -l` and got permission errors trying to access `/proc/asound/` to see any processes associated with ALSA or any kind of audio. 

So for now, local hardware only.
