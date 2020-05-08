**Localization**

Overview
---
The goals / steps of this project are the following:

* Implement a localizer using histograms and Gaussian distributions with additional sensor data to improve the belief of where a car thinks it is on a map.

[//]: # (Image References)
[image0]: ./images/initial_belief.png "Initial"
[image1]: ./images/belief_after_simulation.png "Simulation"
[image2]: ./images/result.png "Result"

---

The code for this project is contained in the file: "Localizer.py" 

### Writeup / README

### Set up world

First we define a 5x5 robot world as well as some other parameters and then create a simulation and shows the initial beliefs of the robot.

The red star shows the robot's true position. The blue circles indicate the strength of the robot's belief that it is at any particular location.

As seen below uniform maximum confusion is applied, which is used to model the confusion of where the robot might be. It assigns equal weight to every possible location in the world

![alt text][image0]

#### Simulate

Next, we use a random generator to move the robot. Ideally we want the biggest blue circle to be at the same position as the red star. Bigger circle indicates a stronger belief.

![alt text][image1]

#### Sense and Move Environment

Then, we create a sense and move function.

These functions consider the posterior belief which are measurements from sensors of an obstacle or distinct landmark in the world create an increased belief (high probability distribution) that it is located next to the landmark/obstacle and a decreased belief (low probability distribution) when it isn't. 

As robot moves, shift belief (probability distribution), convolution.

#### Result

Then, we multiply prior belief (posterior) with convolution to create a distribution that focuses most of its weight on the correct hypothesis of being at the landmark/obstacle

![alt text][image2]

---

### Discussion

#### Known Bugs

•    This tells us that line 40 (in the move function) is causing an IndexError because "list index out of range".

#### Possible Fixes
