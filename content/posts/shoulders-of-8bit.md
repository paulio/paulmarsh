---
title: "Standing on the shoulders of 8-bit giants - what makes a good game?"
date: 2021-04-12T08:58:27+01:00
draft: false
---

<img src="https://miro.medium.com/max/875/1*RSxv-c8gkdfoHzaGljcruA.gif"/>

Recently I was asked to solve a puzzle. I was faced with a very quick demo of a game that I did not recognize, and I was asked how it was done.
It was a fun challenge, but it started me thinking about if classic 8-bit arcade games had anything to offer us today.
There are a lot of really good 8-bit (or at least retro) games, true there are some stinkers too, but is there anything retro games can offer us today?

<!--more-->

## Game Play
First and foremost their game play is fun, but what makes them "fun"? I concede that for me some of the fun is probably blurred by nostalgia.
I remember how novel Space Invaders was or seeing the first scrolling space shooter. Space Invaders is a great example, because whilst it is fun to play again for 10 minutes it does become a little boring to play. What games did, and still can, hold my attention?

## Limited Resources
The second aspect of retro, especially 8-bit, games is they had very limited resources. Early Space Invaders games could only have 2 colours, they used to physically colour the screen to provide some sort of special effect - fortunately, they quickly overcame that technical constraint. But one problem they all shared was a lack of raw processing power and memory, certainly in comparison to modern PCs & Consoles - a modern dishwasher display probably has more potential. But with constraints comes optimisations, clever design, re-use and efficiency. When I consider the aforementioned challenge I was set, it transpired the original game was called Qix. 
<img src="https://miro.medium.com/max/275/1*shSblMy1Gu8Di0f6592ZVQ.png"/>

The game requires the player moves a little 'turtle' around the screen that draws a line. When the turtle meets an existing line, it fills in the shape with a solid colour. My initial thoughts were around edge-detection algorithms and quite complicated scenarios. When I eventually found out the original game was Qix I realised two important things; 1) the scenarios were a lot simpler than I had cooked up 2) this was an 8-bit game, it seemed highly unlikely it was carrying out sophisticated edge detection algorithms in real-time. From that moment I quickly realised not only what the solution was, but also how they had incorporated problems with the solution into the game design. For example, the game requires you fill in 75% of the area, nothing wrong with that, seems like a good game mechanic. But the solution for detecting what area to fill becomes tricky once you approach filling up the whole screen - hence you allow the level to be completed before it becomes an issue. The lessons I have taken away are a) your game can appear sophisticated without requiring large processing - I guess you could call this smoke-and-mirrors b) a clever design can turn problems into advantages.

## Scrolling Shoot-Em-Ups
To investigate what games can still hold my attention I narrowed my search to a genre of game known as 'Scrolling Shoot-Em-Ups'. But before I delve into this genre it is worth looking at what separates them from static games like Space Invaders or Galaxians. 

<img src="https://miro.medium.com/max/571/1*EiPORk5PK0XTzaODWAGV3Q.png"/>
I think of the evolution of these games as being almost linear. Space Invaders had a static screen, that itself evolved to colour, where the enemy moved predictably down the screen. Galaxians evolution was to make it far harder to predict the enemy attacks. The game is more interesting because it is not as monotonous as Space Invaders, the player feels more challenged

**NOTE 1 Challenge the player.**

However, besides a nice little starfield effect Galaxians eventually suffers from the same problem, the game does not really alter, it just gets faster. 
Games like Defender and Scramble introduced horizontal scrolling and a sense of a landscape too.
They also introduced the idea of other controls rather than just move and shoot.
<img src="https://miro.medium.com/max/350/1*uJmPE6bDddB7WbnyQsHwjQ.png"/>

Defender had a mini-map and some humans to rescue. It was a great game but very difficult to survive. Great for the arcade wanting more money, not so great for a spotty teen with little or no money.

**NOTE 2 Appeal to the player's sensibilities, rescuing people and defending your land, but do not make it too hard.**

<img src="https://miro.medium.com/max/291/1*eVocX01xsPlJFwV9M0Q5Ow.png"/>
Scramble has a lot of nice features to consider. It is a horizontal scroller that provides discovery and the concept of an ever-depleting resource - in this case fuel. Discovery is such an important part of a game. As you play to discover new challenging terrain (you can crash into the ground), you discover where the enemy is going to ambush you, you discover where the refuel items are located and you get more complicated enemies as the levels continue. Importantly you are also shown your progress along the map, so if you run out of ships at level 4 you know that if you just played again, you could discover what level 5 was like and then whatever 'base' (see image) is. Scramble also has two different fire mechanisms, a horizontal bullet and a bomb that is dropped on a basic trajectory. 

**NOTE 3 - Alternative Fire**, 

**NOTE 4 - Discovery**

<img src="https://miro.medium.com/max/209/1*Ihr-0Sijgh1S3myUqCu0Sw.png"/>
I was a little reticent to even show Sega's Zaxxon because wow…it is just crazy to see what they managed in 1982. I would consider it to be a 3D/Isometric version of Scramble. But I do remember seeing it and being taken aback. Unfortunately, the 3D-ness made for a slightly uncomfortable hit detection and a small real-estate, so it never became a favourite of mine. 

Jumping ahead a little to a classic vertical scrolling game, 1942.

<img src="https://miro.medium.com/max/275/1*lFpnrNCkjPRkBrKmh1oDfQ.png"/>

This has pretty much all the features you would expect in a modern shoot-em-up. You have the discovery, which is now a given, but it adds several concepts over little old Scramble. Probably the most important is the Power-Up. By collecting (crashing into) power ups the player's ship has additional powers, e.g. rather than firing one shot it now fires 4 at a time.

**NOTE 5 - Power-ups**

What is interesting about Power-Ups is as the game gets progressively harder (more enemies, smarter enemies) you need the Power-Ups to be successful. However, if you lose a life then you typically also lose all your Power-Ups. It adds a level of tension and jeopardy that non-power-up games lack. As mentioned, the enemies are more interesting too. Some take many hits but are slow, some can fire in different directions, and some move in circular patterns, that all combine to make it challenging and fun to play.

**NOTE 6 - Diversity of enemy**

## What should I try and emulate?
There are many games that fulfil several points that I think make a good game. Nemesis (Gradius), Slap-Fight, R-Type are all worthy of investigation with some great implementations of weapon power-ups and enemies. 
<img src="https://miro.medium.com/max/875/1*8M8tAdnVEbuoUGdga7IaOg.png"/>

Whilst Nemesis is widely regarded as an important milestone in the genre, it was proceeded by one of my all-time favourite games; Atari's Xevious.
<img src="https://miro.medium.com/max/875/1*L__k2ucR4OjMhzV9O26mZw.png"/>

I think Xevious was well ahead of its time for 1983. Comparing it with my notes so far it meets a number of them;
1.	Challenge the player - it is quite tricky to play
2.	Appeal to the player's sensibilities - meh, apart from just stopping the baddies, not so much
3.	Alternative Fire - vertical bullets and an interesting bomb reticule
4.	Discovery - lovely scrolling background and interesting layouts of targets and enemies
5.	Power-ups - No, no power-ups here
6.	Enemy Diversity - lots of interesting enemies and 3D effects

Given it was developed in 1983 it makes it an appealing challenge for me.

## Challenge - Unity Xevious

First off, I want to see if I can recreate Xevious, do not worry Atari I am not going to sell it. It will be interesting to see how close I can get and how to cope with different screen sizes, control schemes, etc. One area that always interests me with anything UI based, is how easy is it for a designer to work with. I cannot imagine the original Xevious was a simple drag and drop development, "Yes can I just have that tank moving along that path there". I expect it was a large number of drawings and just getting something to work. So can I design a more designer friendly framework for it? 
Assuming I can get close to the original what can I do to improve it? Will adding the missing points from my list make the game better?
* a nice back story, maybe a prison break
* power-ups, shields, homing bombs, etc.
* network co-op mode
* post-processing effects
* multi-platform build

I am starting up my Solvalou starship, come and join for me the ride.