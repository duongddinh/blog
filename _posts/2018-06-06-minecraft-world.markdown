---
layout: post
title: How big is the minecraft world
date: 2018-06-06 15:47:15 +0300
description: How big is the minecraft world and how long will it take to travel around the world? # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Minecraft, time, big, travel]
---

___________________________________________________


# How big is the minecraft world and how long will it take to travel around the world?

## Using classical physics technique

#### First, starts with gravity.

```java
h = 1/2gt^2 
g = 2*h/t^2
```
where "g" is gravitational acceleration (m/s^2); "h" is height (m), and "t" is time (t). 

![Imgur](https://i.imgur.com/NQUOdhV.jpg)

Each block in minecraft is 1x1x1 (m^3), so we can build to a certain height and measure the time (in seconds) it takes to jump down, image above (Do this multiple times). 

I found that the time for 50m-jump is 2.20 seconds so g is ~_**20.66 m/s^2**_ whereas on earth is ~_**9.8 m/s^2**_

#### Second, calculate the radius/mass.

using the universal gravitation equation:

```java
mg = (G*M*m)/r^2
g = G*M/r^2

```
where "g" is gravitational acceleration (m/s^2); "r" is radius (m); "M" is mass of the planet(kg); "m" is mass of the object (kg), "G" is Universal constant - 6.674×10^−11 - (N·kg^–2·m^2).

gMinecraft is 20.66 and gEarth is 9.8 -> gMinecraft = 2.11 * gEarth

```java
2.11*gEarth = gMinecraft

2.11 * (G*Mass_earth/radius_earth^2) = gMinecraft

```
-> either Mass of Minecraft world is 2.11 times bigger than the mass of earth or the radius of the planet is 0.69 (1/square root of 2.11) times bigger than that of earth.

The mass of minecraft world is 2.11* 5.972 × 10^24 = _**12.60092 x 10^24 kg**_ or the radius of minecraft world is 0.69* 6371000 = _**4395990.0 m**_.

#### With everything above, we can find how many diamonds/emeralds/blocks and how long will it take to travel around the world

(If minecraft world is NOT flat)

###### First, we need to find the volume 

```java
(4*rMinecraft*rMinecraft*rMinecraft*Math.PI)/3;

```

the volume is _**3.558432210460817E20**_ or _**3.56x10^20**_ m^3

the volume of a block in minecraft is 1x1x1 = 1 m^3 

so, there are 3.56x10^20 / 1 = _**3.558432210460817E20**_ or _**3.56x10^20**_ blocks in minecraft.

There are 3.097 blocks of diamond in a chunk and 0.2 blocks of emerald in a chunk; a chunk contains 65536 blocks. 

Using the information above, we can find how many chunks in minecraft using 3.56x10^20 / 65536.
As a result, there are total total_chunk * 3.097 = _**1.6815894402766646E16**_ / _**1.7 x 10^16**_ blocks of diamonds and 
total_chunk * 0.2 = _**1.0859473298525442E15**_ or _**1.1 x 10^15**_ blocks of emerald.

###### how long it takes to travel around minecraft world?

Thinking of it as a circle with radius = 4395990.0, we can find the perimeter of a minecraft world

```java
Math.PI*rMinecraft*2;

```
-> the perimeter is _**2.762081978E7**_ or _**2.8x10^7**_ m

Now, we need to calculate the speed by using how many blocks per time (do this multiple times).

The time to fly (I use flying because it is the fastest way to travel) 10 blocks is 0.87 seconds, so the speed is ~ 11m/s

```java
S = v*t

```

-> t = S/v = 2.8x10^7 / 11 = _**2403011.32 seconds**_ or _**40050.19 minutes**_ or _**667.5 hours**_ or _**27.81 days**_ or _**3.97 weeks**_ or _**0.93 months**_ or _**0.08 years**_ to go one circle around Minecraft world


##### Conclusion

nearly 4 weeks to go one circle around Minecraft world?!
 With that said, I think the mass of minecraft world is 2.11 times bigger than that of earth. In addition, the minecraft world is **flat** - if you dig down, you will see the end but not the other half of the world (image below). 

![Imgur](https://i.imgur.com/TdH30rn.jpg)

[This is the program I wrote for this](https://gist.githubusercontent.com/frychicken/4e108bb8804e88c2c93ec17163289922/raw/e69c8a5176f17e7aab13121535c1183acea14033/Calc_Mine.java)