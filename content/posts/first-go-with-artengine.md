---
title: "First Go With ArtEngine"
date: 2020-07-10T11:20:54+01:00
draft: false
---
First off, I know almost nothing about Art Engine so the fact I could get it to do some useful stuff in next to no time is a good start. This blog post is about what I tried.
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d80a20b6af5d4fef7614%2F5ee8d80a20b6af5d4fef7614_58946.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=632419e696aab8957cf5272c4b92ccf5"/>

<!--more-->

## Changing an Image
I started with a simple image from a photograph I'd taken on my mobile phone;

<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d83cbb9d465dbf17ea0d%2F5ee8d83cbb9d465dbf17ea0d_22825.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=3095d69ae71ab7b15b57e42439ab5773" />

It's not a square, it's pretty low res. So using Art Engines canvas I resized it and up-scaled it.

<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d8bb15e617584ce72320%2F5ee8d8bb15e617584ce72320_22390.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=914214ad4155b10be848d0e921a8dcb4"/>

## Create a Material

Next up, from just a single hi-res pic I used various Material nodes to generate the Normal, Albedo, Height, Metalness and Ambient Occlusion materials from it.

<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d92215e617584ce72330%2F5ee8d92215e617584ce72330_73849.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=216077ef6dd44dedcecc9432e5d16ba7" />

So we have material from a pretty average picture in about 2 mins :)

## Tiling a Material
The problem is that the source image doesn't tile very well;
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d9919017905986465a8d%2F5ee8d9919017905986465a8d_32556.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=9292f6fcda00e71a768d7942352f8e34"/>

No fear, Art Engine node is here to save the day, one node later...
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d9c69505c163fc4b4699%2F5ee8d9c69505c163fc4b4699_81688.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=e527247ecd1e846cd506fd91aea639c5" />

It's not just the diffuse channel either, it works its magic on all of them...
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d9eb034aee5363b751ce%2F5ee8d9eb034aee5363b751ce_8997.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=86aeeb9c1b52468c9b73e04e1f2ccc9d" />

to
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8d9f59505c163fc4b46a0%2F5ee8d9f59505c163fc4b46a0_71455.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=d2e4f2039e9f263dacb82fc699ffb979" />

It took me about 2 mins to setup, maybe another 1 mins or so to run. I can't imagine how much faffing it would traditionally take me.

## Mutating
So we pat on ourselves on the back because we've gone from a humble camera phone picture to a nicely tiling material. But wait, if you like the material, why not have some variations of it? Well okay, grab your Mutate node and create another texture.

<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8dac2ea389c5ad39cef9b%2F5ee8dac2ea389c5ad39cef9b_8619.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=8a35f7a6a5a66ad0e39b220b307877f7" />

Original Material;
<img alt="Original Material" src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8dace4ad53250a3a0257b%2F5ee8dace4ad53250a3a0257b_77518.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=8f082c2f18d1f47d7715a5ca4dec1819" />

Mutation of Material;
<img src="https://t-images.imgix.net/https%3A%2F%2Fstatic.t-cdn.net%2F5dccae9e067deb2d2d704ff2%2Fposts%2F5ee8dadc25e5835a6c38e5cb%2F5ee8dadc25e5835a6c38e5cb_32767.png?width=1240&w=1240&auto=format%2Ccompress&ixlib=js-2.3.1&s=0326ffba75dbd68c7808775e6f8e886f" />

Another material in next to no-time. 

## Summary
Even with just scratching on the surface this tool from Unity looks promising, very promising.

