---
layout: post
title: Math in Simulation
date: 2019-09-26 15:47:15 +0300
description: How I use Math to write a simulation which includes neural network and pool simulation. # Add post description (optional)
img: mathinsim.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [simulation, Math, pool, table, bezier, quadratic, equation, Calculus, neural, network, microevolution, macroevolution]
---

# Pool Table Simulation

This is originally created in addition to a [AP Calculus final project](https://docs.google.com/document/d/1GnH2f1MJIVFp0ZecxBucmMfKm_xlQ4ZAMjXRa4WxazQ), which is the Luigi's curve table problem. I wrote this to support my research as well as my solution (though not required) even though it took 3 months after the solution is written and is submitted. 

The purpose of this program is to simulate a unique pool table known as the curve pool table. The objective is to shoot a ball in such a way that it hits the cushion on the parabolic side and bounces back directly over the same starting spot. One crucial aspect of this parabolic pool table is that the program only requires the width and height of the table as input (as it may be challenging for individuals to deduce the quadratic equation solely from observing the curve). Consequently, the program generates a quadratic equation based on the provided width and length of the curve. This equation is then used to calculate the slope and coordinates of the reflection path.

Generating the curve is a straightforward process, utilizing the concept of a Bezier curve. However, calculating the reflection path poses a more significant challenge. To accomplish this, I employ the slope-line equation, utilizing the x and y coordinates of the ball's current position and the x and y coordinates of its intended destination. Thankfully, Java, the programming language, conveniently provides the mouse's coordinates when it interacts with the frame. Using this information, I can calculate the slope between the initial and projected points by determining the dy/dx ratio.

Using the general equation of a quadratic curve --  y= ax^2 + h -- I use “w” as the width of the table and “h” is the length of the parabola and “a” is the slope or how the curve stretches (figure above). Since we don’t know “a” (the slope) and it is, perhaps, the most important component to calculate the reflection path, we have to find “a” in relation to “w” and “h”. So, this is how I solve for “a”:
At x = w/2, y = 0   
 0=a(w/2)^2+h  a=-4h/w^2 

With that aspect clarified, I primarily utilize the slope-line equation to calculate the reflection path. I generate an additional line known as the tangent line, which possesses the same slope as a point on the curve (specifically, the spot where the ball will hit the cushion). From this line, I create another line perpendicular to the tangent line at the point of impact. Applying basic principles of physics, the angle of the reflection path matches that of the projecting path. Consequently, when the angles are equal, the distances between the lines are also equal due to the properties of an equilateral triangle. Solving for the reflection path becomes a straightforward task.

However, here lies the challenge: drawing all the normal lines is not an easy feat, especially when dealing with extraneous information and lacking the necessary components to create an actual line. Therefore, accomplishing this task requires some ingenuity and workaround. While I possess the starting coordinates and the irrelevant slope, I do not have the ending coordinates. Consequently, I resort to employing very large numbers (-50000 and 50000) in the coordinate system to ascertain the slope and draw the line effectively.

[Link to that program](https://null0verflow.xyz/oldindex.html)

The pool table program takes me a lot of time (approximately a month to complete). The hardest part is often thinking of a way to calculate and draw the reflection path because the surface is not flat. The idea of how to calculate it came unexpectedly in my dream. 

# Neural network 

[the program can be played here](http://research.null0verflow.xyz/)

[open-sourced simple neural network](https://gist.github.com/frychicken/47e5d6e7b9630e1183f1565a4a86e648?fbclid=IwAR3zVUbxvbgzEzR4PQFs6bW9iQvbQ5hDygkRCl49yzE_KA9tRv8EAPNHiU0)

This program is not open-sourced (yet)

I wrote this program when I was 16 years old.

After conducting extensive research, I implemented the Sigmoid Activation function and utilized feedforward calculations to predict output. I employed backpropagation techniques to update weights in this program, which consists of 2 layers, including one hidden layer. For the backpropagation process, I selected the longest-lived balls. The intelligence of a ball is determined by the previous generation and mutation. Random number generation is employed for mutation purposes.

### Mutation-dependant

The program includes a mutation-dependent feature where the survival of a species is predominantly influenced by mutation and mitosis. Each individual undergoes microevolution through an infinite series of mutations, aiming to reach the perfect gene. However, this process lacks genetic diversity, resulting in individuals with generally lower intelligence. Mutations can have both negative and positive effects, making it uncertain whether the next generation will surpass the previous one. Nevertheless, over time, a generation best suited to the environment will emerge, thanks to the workings of natural selection. The program's purpose is to enable the next generation to learn from its predecessors. Mutations will occur in the best-performing trait found in the individual that has progressed the furthest

### Crossover-driven

What happens when there are multiple individuals with unique traits? Crossover occurs, resulting in offspring that inherit traits from both parents. Mutation continues to happen but on a larger scale. As a result, individuals are generally smarter and more diverse, leading to a more stable population. They are able to learn faster, exhibit greater intelligence, and require fewer generations to adapt.

Observing the simulation, after several runs, the balls (referring to the simulated entities) demonstrate survival skills within approximately 3-4 generations, which is significantly faster than the first program (which could take anywhere between 1-200 runs due to the unpredictable nature of mutation). The balls exhibit a combination of their parents' appearances, with the color being averaged between the dad and mom. While I didn't fully grasp neural networks, I was determined to complete what I had started. Motivated by this desire, I began coding from scratch and completed the task within less than 24 hours. The lesson learned here is to not overlook the basics, as they form the foundation for more advanced concepts.

Genetic variation is incredibly crucial. It serves as the primary catalyst for a stable environment and growth. Let us strive to conserve species and protect the environment. We are currently facing the sixth mass extinction, and this time, humanity itself is the meteor.

This program is written in java (It is a _very_ simple program with a simple neural network. Brains except uno input and decide whether to jump or not. Brains will accept more inputs --up to 3-- soon). Keep in mind that not everyone is born stupid; hence, you may need to re-run multiple times (possibility of a smart individual is 3/10, and possibility of all-are-smart is 0.027).

# Bottom line 

I have gained invaluable knowledge through programming these two programs, which has strengthened my understanding of math, physics, and biology. It is easy to overlook the importance of these subjects in school, as we are often required to learn them without choice. I used to question their relevance in real life as a child, thinking, 'When will I ever need this? I don't want to study another day without using y=ax+b.' However, as I grew older, I became obsessed with creating both tangible and intangible things. This raises an issue: if schools were to do a better job of teaching and demonstrating the practicality of these subjects, it would foster a greater appreciation for the world among students. I can confidently say that I have taught myself more than what school has taught me. Nonetheless, the one positive aspect of school is the social experience it offers.
