---
title: "Ev3 Projects: Car Following"
author: "Rohan Arni"
date: 2022-03-16T01:41:07.050Z
lastmod: 2023-01-03T17:49:20-05:00

description: ""

subtitle: "This article is about a project I did with my Ev3 robot in which I made my Ev3 robot follow a toy car. This is similar to some features…"

image: "/posts/2022-03-16_ev3-projects-car-following/images/1.jpeg" 
images:
 - "/posts/2022-03-16_ev3-projects-car-following/images/1.jpeg"
 - "/posts/2022-03-16_ev3-projects-car-following/images/2.jpeg"


aliases:
    - "/ev3-projects-car-following-8d98960310db"

---

This article is about a project I did with my Ev3 robot in which I made my Ev3 robot follow a toy car. This is similar to some features that many modern cars have today known as adaptive cruise control.. Let’s break this project down into three aspects: the thought process, the hardware, and the software.

The thought process is quite simple. I was inspired by my parents’ car, the Lexus RX 350. It has a feature that follows the car in front of it by keeping a constant distance from the other car. It can also speed up and down based on the speed of the other car. I thought that this would be quite easy to model with the Ev3 using principles from the PID line following algorithm. PID is an algorithm that “proportionally” follows a line. (I made a PID line follower on Github, which you can check out [here](https://github.com/rtenacity/LineFollower)) The algorithm uses how far away the robot is from the line to judge how much the robot should turn. Using the idea of proportionally following a target, I thought instead of following a line, I could make the robot follow a car.

The physical aspect of the robot is quite simple. I built a car that was modeled behind a formula one car (for the cool factor). It has an ultrasonic sensor on the front part of the car and a touch sensor on the back. The robot also has two large motors in the back for driving, and also has steering capabilities using the medium motor. However, I have disabled the steering capabilities to prevent the robot from veering.

![image](/posts/2022-03-16_ev3-projects-car-following/images/1.jpeg#layoutTextWidth)
Side view


![image](/posts/2022-03-16_ev3-projects-car-following/images/2.jpeg#layoutTextWidth)
Top view



Now, let’s break down the code. The code can be found at my repository [here](https://github.com/rtenacity/CarFollower).
`#!/usr/bin/python  
# coding: utf-8  

# this program lets your ev3 follow a toy car accurately  

from ev3dev2.motor import *  
from ev3dev2.sensor.lego import UltrasonicSensor, GyroSensor, InfraredSensor, TouchSensor  
from ev3dev2.led import Leds  
from ev3dev2.sound import Sound  
from sys import stderr  
from time import sleep`

These lines are just imports from the necessary libraries.
`left_motor = LargeMotor(OUTPUT_C)   
right_motor = LargeMotor(OUTPUT_D)  
us = UltrasonicSensor()  
ts = TouchSensor()`

These lines are just so that I can reference these items easily later in the program.
`correction = 0  

kp = 1   
power = 60  
target = 10`

This is where things begin to get interesting. The variable **correction** is just a blank variable for now. This will be used later in the program.

The variable **kp**, also known as the “constant of proportionality”, is the factor which changes how sharp the movement is. I’ve left it as the default value of 1.

**Power** is the base speed of the car. I’ve set it to 60, which means that the motor is going at 60% full power as a baseline.

**Target** is the target range from the toy car to the Ev3. I’ve set it to 10 cm.
`left_motor.run_direct()  
right_motor.run_direct()`

These lines start the motors.
`while True:  
    error = target - us.distance_centimeters`

**Error** is the difference between the target value and the distance value. This will come in handy for the **proportional** line following.
`if ts.value():  
        break`

This line turns the touch sensor into a killswitch by breaking out of the while true loop.
`if error &lt; 0:   
        correction = (abs(float(error)/5))*kp  
        if (correction+power) &gt;= 100 or (correction+power) &lt;= -100:   
            correction = -(power)`

If **error** is less than 0, the Ev3 is too far from the car. The variable **correction** is **error** divided by 5 multiplied by the **kp** (constant of proportionality). **Correction** is added to **power** to change the final wheel speed, which speeds up the car (not shown here).

The second if statement is just to make sure the final wheel speed is not above 100 or less than -100, otherwise the robot will error out.
`if error &gt; 0:  
        correction = -(power)`

If **error** is more than 0, the Ev3 is too close to the car. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
`if error == 0:   
        correction = -(power)`

If **error** is equal than 0, the Ev3 is the perfect distance from the car, which makes the Ev3 stop. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
`if us.distance_centimeters == 255.0:  
        correction = -(power)`

The ultrasonic sensor has an error where it randomly reads 255 cm, so this line makes sure it doesn’t glitch out and mess up the algorithm by making the car stop. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
`print(str(target)+&#34;, &#34;+str(us.distance_centimeters)+&#34;, &#34;+str(error)+&#34;, &#34;+str(correction)) `

This line is for debugging. It prints out the values of each of the important variables to figure out any issues with the robot.
`left_motor.duty_cycle_sp= int(-(power + correction)) right_motor.duty_cycle_sp= int(-(power + correction)) `

These lines set the final wheel speed. I made the value negative because my robot’s wheels are backward.
`sleep(0.1)`

This line makes sure that the CPU doesn’t overheat.
`left_motor.stop()  
right_motor.stop()`

When the touch sensor breaks the loop, these lines make sure that the robot’s motors stop.

And that’s it! Here’s a video of the robot in action:




Ev3 in action



Thanks for reading! I hope you enjoyed this article.

Note from the author: Hello there! It’s been a while. I’ve been pretty busy with school and other things, but now I’m back. I have multiple articles planned for the future.
