---
title: Counterstrike Devops
date: 2024-10-14 12:43:09
tags: [counterstrike, csharp, counterstrikesharp, source2, gamedev, linux]
categories: [CounterStrike, C#]
toc: true
---

This is an outline of how I built a CI system to develop Counter Strike 2 plugins, complete with an automated build system and local test server.

# Context

Counter Strike 2 is a 5v5 first-person shooter video game played by <a href="https://steamcharts.com/app/730">over a million people a day</a> (at the time of writing). The game's architecture is client-server, meaning the players connect to a central server hosted somewhere between them, on which the game itself is played. This server binary is provided by Valve, the makers of Counter Strike, free of charge for anyone to download and run their own server. 

In addition to being able to run your own local server to host the game, there is a project called <a href="https://cssharp.dev">Counter Strike Sharp</a> which distributes a C# package exposing a number of useful API's that can be used to write creative mods for the game (called "plugins") that run on the server-side.

# Server Setup

The first thing we must do before anything else is set up a plain old Counter Strike server on a local machine. 

Counter Strike has historically iterated versions alongside its engine - first GoldSrc in 1999, a heavily modified Quake engine used to make the original Counter Strike (as well as Half-Life)

I use set of bash scripts known as <a href="https://linuxgsm.com">LinuxGSM</a> to do this. LGSM is an open-source project by a very talented developer, <a href="https://danielgibbs.co.uk/">Dan Gibbs</a>. It greatly simplifies the process of configuring a basic server for over 120 self-hostable games on Steam.

-wip-
