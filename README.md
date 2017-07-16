# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Introduction

The objective of this project was to "build a PID controller and tune the P,I and D hyperparameters by applying the techniques as described in the lessons," and test the  solution on the simulator . The simulator provides cross-track error (CTE), speed, and steering angle data via local websocket. The PID (proportional/integral/differential) controller must respond with steering and throttle commands to drive the car  around the simulator track in a stable manner .

## Reflection

### Describe the effect each of the P, I, D components had in your implementation.

The P component is the propotional controller. It changes steering angle in propotion to the crosstrack error (CTE). With just the P component, I observed that the car oscillated around the center of the track going left and right and eventually  off the track . This is expected since with just the P component, as shown in the lecture the car overshoots and undershoots

The D component is the differential controller. It changes steering in proportion to the derivative of the crosstrack error. The D-component helps dampen the oscillations and with a P and D controller, the car is able to drive around the track though the driving pattern is not very smooth. I think this is also expected behavior because as shown in the lectures with and P and D controller a car is able to follow
the track if there is no steering drift. It seems to drive in a wavy manner along the center of the road. While the driving is not dangerous, its no fun sitting in a car that drives like this 

The I component is the integral controller. It changes steering in proportion to the sum of crosstrack errors. This term is needed to fix any bias in the steering and correct for drift. I added a small integral component. I don’t think there is any material bias in the steering, so I  didn’t have a big impact on the steering 


### Describe how the final hyperparameters were chosen

I chose the P, I and D components through manual tuning. I experimented with just a P controller but that caused the car to oscillate a lot. So I added a D component to dampen the oscillations. I found that the car was able to drive around the track for a lot of values of P and D. I added a small I component but it didn’t seem to have a material impact on driving around the simulator. Higher values of D component, dampened the oscillations more. I also increased the throttle and found that a slightly adjusting the P, I and D components ensured that the car was able to drive around the simulator.

### Video

Below is the url  to the final video output  

### PID_Controller_Ashis.mp4
https://youtu.be/Y06pXsYHKtg


## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!

More information is only accessible by people who are already enrolled in Term 2
of CarND. If you are enrolled, see [the project page](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/f1820894-8322-4bb3-81aa-b26b3c6dcbaf/lessons/e8235395-22dd-4b87-88e0-d108c5e5bbf4/concepts/6a4d8d42-6a04-4aa6-b284-1697c0fd6562)
for instructions and the project rubric.

## Hints!

* You don't have to follow this directory structure, but if you do, your work
  will span all of the .cpp files here. Keep an eye out for TODOs.

## Call for IDE Profiles Pull Requests

Help your fellow students!

We decided to create Makefiles with cmake to keep this project as platform
agnostic as possible. Similarly, we omitted IDE profiles in order to we ensure
that students don't feel pressured to use one IDE or another.

However! I'd love to help people get up and running with their IDEs of choice.
If you've created a profile for an IDE that you think other students would
appreciate, we'd love to have you add the requisite profile files and
instructions to ide_profiles/. For example if you wanted to add a VS Code
profile, you'd add:

* /ide_profiles/vscode/.vscode
* /ide_profiles/vscode/README.md

The README should explain what the profile does, how to take advantage of it,
and how to install it.

Frankly, I've never been involved in a project with multiple IDE profiles
before. I believe the best way to handle this would be to keep them out of the
repo root to avoid clutter. My expectation is that most profiles will include
instructions to copy files to a new location to get picked up by the IDE, but
that's just a guess.

One last note here: regardless of the IDE used, every submitted project must
still be compilable with cmake and make./
