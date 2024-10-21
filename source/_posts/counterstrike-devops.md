---
title: Counterstrike Devops
date: 2024-10-14 12:43:09
tags: [counterstrike, csharp, counterstrikesharp, source2, gamedev, linux]
categories: [CounterStrike, C#]
toc: true
feature: details.png
---

This is an outline of how I built a CI system to develop Counter Strike 2 plugins, complete with an automated build system and local test server.

# Context

Counter Strike 2 is a 5v5 first-person shooter video game played by <a href="https://steamcharts.com/app/730">over a million people a day</a> (at the time of writing). The game's architecture is client-server, meaning the players connect to a central server hosted somewhere between them, on which the game itself is played. This server binary is provided by Valve, the makers of Counter Strike, free of charge for anyone to download and run their own server. 

In addition to being able to run your own local server to host the game, there is a project called <a href="https://cssharp.dev">Counter Strike Sharp</a> which distributes a C# package exposing a number of useful API's that can be used to write creative mods for the game (called "plugins") that run on the server-side.

# Server Setup

The first thing we must do before anything else is set up a plain old Counter Strike server on a local machine. 

I use set of bash scripts known as <a href="https://linuxgsm.com">LinuxGSM</a> to do this. LGSM is an open-source project by a very talented developer, <a href="https://danielgibbs.co.uk/">Dan Gibbs</a>. It greatly simplifies the process of configuring a basic server for over 120 self-hostable games on Steam.

To install LinuxGSM, all you need to do is download and run the <a href=https://linuxgsm.sh>install script</a> in a POSIX-compliant terminal. It's best to just use bash, since this is what LGSM is written in. Granted you have sudo access, the script will also download and install any missing dependencies from the appropriate package registry for your distro.

Download the install script using `curl`:
```bash
curl -Lo linuxgsm.sh https://linuxgsm.sh
```
Grant executable permission:
```bash
chmod +x linuxgsm.sh
```
Run the script with one argument, the name of the gameserver you want to install. In this case, cs2, but you can see the full list of supported games <a href="https://linuxgsm.com/servers/">here</a>.
```bash
bash linuxgsm.sh cs2server
```
LinuxGSM will install the rest of the program that it needs for the game you specified. This is to avoid shipping code for every game when most people just want to host one. There will now be a script in the current directory called `cs2server`. The final step is to have LGSM install SteamCMD and the game binary and set up scripts to start and manage the server. This, too is only one command:
```bash
./cs2server install
```

After some time, possibly a while (CS2 is a big binary and Steam's CDN is <a href="google.com/search?q=steamcmd+slow">notoriously slow</a> with these sorts of downloads), you will have a stock CS2 server ready to start and join, and manage with these scripts.

I won't go into further capabilities of LGSM here but the project is <a href="https://docs.linuxgsm.com">meticulously documented</a> and there is a <a href="https://linuxgsm.com/discord">discord</a> where both myself and other developers on the project provide support for free.

One small note - CS requires very high per-core clock speeds to run a server with a lot of players. Think 4.0ghz and up. Something down to 3.5 will give few issues for local development, however.

# Writing Mods - The Fun Part

-wip-
