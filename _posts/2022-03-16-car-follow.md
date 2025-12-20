---
layout: post
title: Ev3 Projects - Car Following
date: 2022-03-16
description: This article is about a project I did with my Ev3 robot...
categories: robotics ev3
---

 
This article is about a project I did where I made my Ev3 robot follow a toy car. This is similar to some features that many modern cars have today known as adaptive cruise control. Let’s break this project down into three aspects: the thought process, the hardware, and the software.

The thought process is quite simple. I was inspired by my parents’ car, the Lexus RX 350. It has a feature that follows the car in front of it by keeping a constant distance from the other car. It can also speed up and down based on the speed of the other car. I thought that this would be quite easy to model with the Ev3 using principles from the PID line following algorithm. PID is an algorithm that “proportionally” follows a line. (I made a PID line follower on Github, which you can check out [here](https://github.com/rtenacity/LineFollower)) The algorithm uses how far away the robot is from the line to judge how much the robot should turn. Using the idea of proportionally following a target, I thought instead of following a line, I could make the robot follow a car.

The physical aspect of the robot is quite simple. I built a car that was modeled behind a formula one car (for the cool factor). It has an ultrasonic sensor on the front part of the car and a touch sensor on the back. The robot also has two large motors in the back for driving, and also has steering capabilities using the medium motor. However, I have disabled the steering capabilities to prevent the robot from veering.

<div style="max-width: 50%; margin: auto;">
{% include figure.liquid path="assets/img/car-follow/1.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
<p style="text-align: center;">Side view</p>
</div>


<div style="max-width: 50%; margin: auto;">
{% include figure.liquid path="assets/img/car-follow/2.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
<p style="text-align: center;">Top view</p>

</div>


The full video demonstration is below:

<iframe src="https://player.vimeo.com/video/688664126"
        width="640"
        height="360"
        frameborder="0"
        allow="autoplay; fullscreen"
        allowfullscreen
        style="display:block; margin:0 auto;"></iframe>

<br>

Now, let’s break down the code. The code can be found at my repository [here](https://github.com/rtenacity/CarFollower).

{% highlight python linenos %}
#!/usr/bin/python  
# coding: utf-8  
# this program lets your ev3 follow a toy car accurately  

from ev3dev2.motor import *
from ev3dev2.sensor.lego import UltrasonicSensor, GyroSensor, InfraredSensor, TouchSensor  
from ev3dev2.led import Leds  
from ev3dev2.sound import Sound  
from sys import stderr  
from time import sleep

left_motor = LargeMotor(OUTPUT_C)   
right_motor = LargeMotor(OUTPUT_D)  
us = UltrasonicSensor()  
ts = TouchSensor()
{% endhighlight %}



These lines are just so that I can reference these items easily later in the program.
{% highlight python linenos %}
correction = 0  

kp = 1   
power = 60  
target = 10
{% endhighlight %}

This is where things begin to get interesting. The variable **correction** is just a blank variable for now. This will be used later in the program.

The variable **kp**, also known as the “constant of proportionality”, is the factor which changes how sharp the movement is. I’ve left it as the default value of 1.

**Power** is the base speed of the car. I’ve set it to 60, which means that the motor is going at 60% full power as a baseline.

**Target** is the target range from the toy car to the Ev3. I’ve set it to 10 cm.
{% highlight python linenos %}
left_motor.run_direct()  
right_motor.run_direct()
{% endhighlight %}

These lines start the motors.
{% highlight python linenos %}
while True:  
    error = target - us.distance_centimeters
{% endhighlight %}

**Error** is the difference between the target value and the distance value. This will come in handy for the **proportional** line following.
{% highlight python linenos %}
if ts.value():  
        break
{% endhighlight %}

This line turns the touch sensor into a killswitch by breaking out of the while true loop.
{% highlight python linenos %}
if error < 0:   
        correction = (abs(float(error)/5))*kp  
        if (correction+power) >= 100 or (correction+power) <= -100:   
            correction = -(power)
{% endhighlight %}

If **error** is less than 0, the Ev3 is too far from the car. The variable **correction** is **error** divided by 5 multiplied by the **kp** (constant of proportionality). **Correction** is added to **power** to change the final wheel speed, which speeds up the car (not shown here).

The second if statement is just to make sure the final wheel speed is not above 100 or less than -100, otherwise the robot will error out.
{% highlight python linenos %}
if error > 0:  
        correction = -(power)
{% endhighlight %}

If **error** is more than 0, the Ev3 is too close to the car. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
{% highlight python linenos %}
if error == 0:   
        correction = -(power)
{% endhighlight %}

If **error** is equal than 0, the Ev3 is the perfect distance from the car, which makes the Ev3 stop. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
{% highlight python linenos %}
if us.distance_centimeters == 255.0:  
        correction = -(power)
{% endhighlight %}

The ultrasonic sensor has an error where it randomly reads 255 cm, so this line makes sure it doesn’t glitch out and mess up the algorithm by making the car stop. The car stops by making **correction** the inverse of **power**, which makes the final wheel speed equal to 0.
{% highlight python linenos %}
print(f"{target}, {us.distance_centimeters}, {error}, {correction}")
{% endhighlight %}

This line is for debugging. It prints out the values of each of the important variables to figure out any issues with the robot.
{% highlight python linenos %}
left_motor.duty_cycle_sp= int(-(power + correction)) right_motor.duty_cycle_sp= int(-(power + correction)) 
{% endhighlight %}

These lines set the final wheel speed. I made the value negative because my robot’s wheels are backward.
{% highlight python linenos %}
sleep(0.1)
{% endhighlight %}

This line makes sure that the CPU doesn’t overheat.
{% highlight python linenos %}
left_motor.stop()  
right_motor.stop()
{% endhighlight %}

When the touch sensor breaks the loop, these lines make sure that the robot’s motors stop.

And that’s it!