---
layout: post
title: Math in Simulation
date: 2019-09-26 15:47:15 +0300
description: How I use Math to write a simulation which includes neural network and pool simulation. # Add post description (optional)
img: # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [simulation, Math, pool, table, bezier, quadratic, equation, Calculus, neural, network, microevolution, macroevolution]
---

# Pool Table Simulation

This is originally created in addition to a [AP Calculus final project](https://docs.google.com/document/d/1GnH2f1MJIVFp0ZecxBucmMfKm_xlQ4ZAMjXRa4WxazQ), which is the Luigi's curve table problem. I wrote this to support my research as well as my solution (though not required) even though it took 3 months after the solution is written and is submitted. 

This program’s purpose is to create a pool table simulation (not just any typical pool table, but the curve pool table), and that, attempt to shoot a ball in such a way that it hits the cushion in the parabolic side and bounces directly back over the same spot from which it began. One of the important components of this parabolic pool table is that the program only accepts the width and height of the parabolic table (because people cannot come up with the quadratic equation from observations of the curve). Therefore, the program has to generate a quadratic equation based on the width and the length of the curve, which then, calculate the slope and the coordinates of the reflection path.


Generate the curve is simple, using the idea of bezier curve. Yet, calculate the reflection path is quite challenging. I use the slope-line equation to calculate the path of the ball, utilizing x and y of where the ball is placed and x and y of where the ball will be going to. Java, the programming language, conveniently gives you the coordinates of your mouse when the mouse touches the frame. From that, I can calculate the slope of the beginning and ending points (from the origin to the projecting points): dy/dx. 

Using the general equation of a quadratic curve --  y= ax^2 + h -- I use “w” as the width of the table and “h” is the length of the parabola and “a” is the slope or how the curve stretches (figure above). Since we don’t know “a” (the slope) and it is, perhaps, the most important component to calculate the reflection path, we have to find “a” in relation to “w” and “h”. So, this is how I solve for “a”:
At x = w/2, y = 0   
 0=a(w/2)^2+h  a=-4h/w^2 

With that out of the way, I use mainly slope-line equation to calculate the reflection path. I generate another line, this line has the same slope as a point in the curve (tangent line), which is the point (spot) that the ball will be hitting at the line (cushion). From that line, I generate another line which is perpendicular to that line at the point the ball will be hitting. Now, simple physics: the angle of the line of the reflection path is the same as the angle of the line of the projecting path; when the angle equals to each other, the distance between them is also equal as a result of an equilateral triangle. Now solving the reflection path is a piece of cake. Here comes the problem: drawing all the normal lines isn’t easy when you have irrelevant information and barely anything fundamental for creating actual line. Hence, it could not be done (from my knowledge) without chicanery. I know the starting coordinates and the irrelevant slope, but no ending coordinates. Therefore, I have to use a very big number (50000 and -50000) in the coordinates system to find the slope as well as to draw the line. 

[Link to that program](https://null0verflow.xyz/oldindex.html)

The pool table program takes me a lot of time (approximately a month to complete). The hardest part is often thinking of a way to calculate and draw the reflection path because the surface is not flat. The idea of how to calculate it came unexpectedly in my dream. 

# Neural network 

[the program can be played here](http://research.null0verflow.xyz/)

[open-sourced simple neural network](https://gist.github.com/frychicken/47e5d6e7b9630e1183f1565a4a86e648?fbclid=IwAR3zVUbxvbgzEzR4PQFs6bW9iQvbQ5hDygkRCl49yzE_KA9tRv8EAPNHiU0)

This program is not open-sourced (yet)

I was 16 when this program is written. 

After a lot of research, I use Sigmoid Activation function, feedforward to calculate predicted output and backpropagation techniques to update weights. This program only has 2 layers and one hidden layer. The longest lived balls will be used for backpropagation. How smart a ball is depend on the previous generation and mutation. I use random number generator for mutation.

### Mutation-dependant

The program has a mutation-dependent option where the species survivability largely depends on mutation and mitosis. It is just an individual undergoing microevolution through infinite mutation to arrive at the perfect gene. There is no genetic diversity. This generally means less-smart individual. Mutation could be both bad and good; it is uncertain that the next generation is better than the previous generation. However, ultimately, there is gonna be one generation best fit to the environment (Natural selection doing its job). The program's job is to make the next generation learn from the previous generation. The mutation will occur in the best trait (individual who goes the furthest) 

### Crossover-driven

What happens if there are more than one? More individuals with unique traits. Crossover happens; they produce offsprings which carry both their parents traits. Mutation still happens but at a larger scale. Therefore, individuals are generally smarter and more diverse. Moreover, the population will be more stable. In general, study faster, smarter and need less generations.

Observing the simulation, after several runs, the balls know how to survive at around 3-4 generation, which is significantly faster than the first program (could be anywhere between 1-200 runs because mutation is unpredictable).
the balls share their parents' looks (average the color of the dad with the mom's). I did not fully understand neural network, yet still wrote the whole program and failed miserably. Recently, neural network came into my head (perhaps I cannot live with my own failure). with the urge to finish what i started, within less than 24 hours, I began coding (but from the ground up). The lesson here is to not skip the basics as it is the groundwork for more advanced things.

Genetic variation is _extremely_ important. It is the primary reason for a stable environment and development. Go save species and plant trees, don't destroy the environment, we are currently in the midst of the 6th mass extinction, and this time, humanity is the meteor.

This program is written in java (It is a _very_ simple program with a simple neural network. Brains except uno input and decide whether to jump or not. Brains will accept more inputs --up to 3-- soon). Keep in mind that not everyone is born stupid; hence, you may need to re-run multiple times (possibility of a smart individual is 3/10, and possibility of all-are-smart is 0.027).

# Bottom line 

I learned a lot from programming these two programs. It reinforces me in my math knowledge, physics as well as biology. It is easy to overlook the important of these subjects in school (largely because we have to learn and it is not a choice). The question I often ask when I was a kid is "when am I gonna need this in real life? I don't want to study, another day of living without using y=ax+b. " And here it is, me being few years older who got obssessed with creating things from tangible to intangible. So here is the problem, if school were to do a better job of teaching and open their kids' eyes in the practicality of the subject, it would make the kids more appreciative of the world around them. I can confidently says that I taught myself more than school has. The one good thing from school is the social experience/life.
