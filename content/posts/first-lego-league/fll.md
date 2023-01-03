---
title: "First Lego League"
author: "Rohan Arni"
date: 2021-02-28
draft: false

categories: ["EV3", "Robotics", "ev3dev"]
---

The Mindstorms Ev3 Robot is a robot made by Lego. So obviously, there are competitions surrounding the robot. I participated in two of them. How did it go? Let’s find out.

Let’s establish some context. My friend invited me to a robotics competition that his dad coached in summer of 2019. It was called First Lego League. It was all about making the Mindstorms Robot move around on this mat and do tasks on the mat, called missions. This is what the mat looked like:

{{<rawhtml>}}
<center>{{< figure src="/img/fll.webp" title="FLL Mat" >}}</center>
{{</rawhtml>}}

As you can see, there are little Lego structures scattered around the mat that the robot must go to and complete missions there. Missions award you points. There are three rounds. The round with the highest points counts. At the end of the he top three teams make it to the next round.

In the 2019–2020 competition, we used something called RobotC to control the Ev3. It was a version of C that the Ev3 understands. Crappy program, always crashed, but it got the job done.

In the 2020–2021 competition however, everything changed. We used something called Ev3Dev, which is a Linux distro for the Ev3. That way, we could use python to control the robot. However, the bootup time for the program is very high. So we used the buttons on the robot to run programs. The way it worked is that you have a main execute script, which links to files that contain the code for all missions. It also connects to a script which processes the button inputs. Here is a diagram showing the way out setup worked:

{{<rawhtml>}}
<center>{{< figure src="/img/fll2.webp" title="Diagram" >}}</center>
{{</rawhtml>}}

<!-- So this is all the software design. Let’s look at the hardware:
{{<rawhtml>}}
<a href = "https://vimeo.com/517806926" > Video of robot </a>
{{</rawhtml>}} -->

Let’s look at the software design.  

This is the launcher code:
~~~
#!/usr/bin/env python3
from ev3dev2.motor import *
from ev3dev2.sensor.lego import *
from ev3dev2.button import *
from ev3dev2.wheel import *
from ev3dev2.sound import *
import library
steering = MoveSteering(OUTPUT_C, OUTPUT_B)
motor = MediumMotor()
tank = MoveTank(OUTPUT_B, OUTPUT_C)
STUD_MM = 8
mdiff = MoveDifferential(OUTPUT_B, OUTPUT_C, EV3Tire, 16 * STUD_MM)
tank.gyro = GyroSensor()
mdiff.gyro = GyroSensor()
btn = Button()
sound = Sound()
sound.play_tone(880, 0.25)
sound.play_tone(440, 0.25)
library.choice(tank, SpeedPercent, follow_for_ms, motor, mdiff, steering,btn, sound)
~~~
This program is fairly simple. It has standard imports, some typical definitions for the robot to run, and then it invokes the choice function from the library. The choice function is the main function that runs the robot. It is defined in the library.py file. Here is the code for the library.py file:
~~~
import bench
import dance
import bottom_right
import step_slide
import stepper
import slide
import input
import treadmil
import treadmil_gate
def choice(tank, SpeedPercent, follow_for_ms, motor, mdiff, steering, btn, sound):
    while True:
        print(“ready for next command”)
        functionNumber = input.readKeys(btn, sound)
        print(functionNumber)
        if functionNumber == 1:
            bench.go(tank)
        elif functionNumber == 2:
            stepper.go(tank, SpeedPercent, follow_for_ms, motor, mdiff)
        elif functionNumber == 3:
            treadmil_gate.go(tank, SpeedPercent, follow_for_ms, motor, mdiff)
        elif functionNumber == 0:
            dance.dance_now(tank, steering)


~~~
The choice function is a launcher for a program that we wrote to complete a mission. We used the buttons on the robot to define the variable `functionNumber`. Depending on the buttons that we pressed, the functionNumber would be different. This may seem extraneous, but this solves a major issue that ev3dev presents. If we were to do this normally and have a different program for each mission, the bootup time would be too long. So we used this launcher to invoke the function for each mission. <br/> Let’s take a look at the code for one of the missions:

{{<rawhtml>}}
<center>{{< figure src="/img/fll3.webp" title="The Stepper" >}}</center>
{{</rawhtml>}}

The goal is to push that green tab into the purple-and-black box.

~~~
from time import sleep
def go(tank, SpeedPercent, follow_for_ms, motor, mdiff):
    #forward fast 63cm
    tank.on_for_rotations(50, 50, 5.0)
#forward slow 20cm
for i in range(33):
    tank.on_for_rotations(5, 5, 0.05)
    sleep(0.03)
#backward fast 32cm
tank.on_for_rotations(-50, -50, 10)
~~~


No imports, as you can see. There is no need for them, as library.py has the imports.

So this whole thing is a function that library invokes. First, the robot uses the tank function, which controls the robot’s wheels as a tank. It goes forward for 5 rotations, which is 63 cm. That takes us close to the stepper contraption. We go slower for 20 cm to push the stepper in using the tank function. Then we back out of there super fast to save time, coming back to the home base.

Thanks for reading!

~~~
print("End of file.")
~~~

*Note from the author: This article was written in 2021 on my old blog on medium. I am reposting it here for archival purposes. This article has been modified to fit the new blog.*