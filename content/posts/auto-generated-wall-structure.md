---
title: "Auto Generated Wall Structure"
date: 2020-07-10T11:31:52+01:00
draft: false
---

I've been developing a script that takes the dimensions of a structure and automatically constructs a prefab of the structure made up of individual destructable bricks. In the latest incarnation I've added an entrance.

<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ed0dfaf073e3b31ec21123a%2F5ed0dfaf073e3b31ec21123a_98046.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=6a32d23a8a20a21abb8fd69e62ebebb8" />
<!--more-->
It exposed quite a few nasty problems. When you have a parent transform that contains a number of other elements then it's really tricky to find its boundary, i.e. what size area does it contain. Short of adding up the size and position of each of its children I couldn't really find a better way of doing it. If anyone has any ideas then great. Any how, the final result isn't too bad. I ended up having to fudge the brick structure above the entrance. In reality you'd continue the same brick...lattice?...from either side but I've actually just adjusted the brick size to fit the specific width of the entrance. It makes the computation of the walls a lot easier. 

Windows next, &lt;gulp>.

PS. Someone should add 'Spreadsheet App' to the list of tools needed to develop in Unity. I'd be lost without mine!