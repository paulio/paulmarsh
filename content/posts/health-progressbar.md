---
title: "Health/Progress bar via a Shader"
date: 2020-07-10T11:01:35+01:00
draft: false
---
It's a fairly common requirement to have some sort of health-bar or progress-bar in a game. However, as explained by [Steve Streeting](https://www.stevestreeting.com/2019/02/22/enemy-health-bars-in-1-draw-call-in-unity) this can have performance problems if you're using a Canvas and assigning it to many entities. The answer is to use a Shader, but what does that look like? This morning I set about trying to create one and this is my result;
<img src="/images/home/HealthShader.png" alt="Health Shader"/>

<!--more-->