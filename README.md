# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---
# Introduction
This project implements a PID controller in C++ to maneuver the vehicle around a track in Udacity simulator. The simulator will provide the cross track error (CTE) and the velocity (mph) in order to compute the appropriate steering angle. The purpose of this project are:

1. build a PID controller and tune the PID hyperparameters by applying the general processing flow
2. test the solution on the simulator

# Rubric
# Compilation
The code compiles without errors or warnings.
# Implementation
The PID procedure follows what was taught in the lessons. The detailed information is given in main.cpp and PID.cpp files.
# Reflection
1. Describe the effect each of the P, I, D components had in your implementation.

The P, or "proportional", tries to steer the car toward the center line. It causes the car to steer proportional to the the CTE. If only P is applied, the car will overshoot the center line and go out of the road track easily. An example video is given in “Video/P.mp4”.

The D, or "differential", helps to counteract the trend to overshoot the center line. A properly tuned D parameter will make the car approach the center line smoothly. An example video is given in "Video/PD.mp4".

The I, or "integral", is to compensate for systematic biases in the CTE which prevents the P-D controller from reaching the center line. In this project it can be found when video "PD" and "PID" are compared, there is no obvious difference. So there may be no obvious systematic bias in this project.

The final PID performance is given in video "Video/PID.mp4". 2. Describe how the final hyperparameters were chosen.
The hyperparameters were chosen manually. First, I find the car can drive straight with 0 as parameters (given in video "Video/without.mp4"). Then I add the “P” and the car start going on following the road but with overshoots. Then I add the “D” to try to overcome the overshoots. Because I find without “I” the controller works already good, and with high value of “I” the car will go out of the road, so I choose very low value of “I”. At last the hyperparameters is adjusted to reduce the cross-track error. The final hyperparameters are (P: 0.2, I: 0.004, D: 3.0).
# Simulation

The vehicle successfully drive a lap around the track which is shown in video "Video/ PID.mp4".

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
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

Fellow students have put together a guide to Windows set-up for the project [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/files/Kidnapped_Vehicle_Windows_Setup.pdf) if the environment you have set up for the Sensor Fusion projects does not work for this project. There's also an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3).

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

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

## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).

