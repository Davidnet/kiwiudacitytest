## Welcome to Kiwi's Self-Driving Kiwibot Simulator

This simulator provides students with a real challenge of being a self driving engineer at Kiwi data science division.

![KiwiBot Challenge](./Challenge.png)


### Objectives

Two tracks, easy track and dangerous curves, are provided to you so you can get familiarized with the communications protocols of the game, also you can test any machine learning implementation or computer vision approach which can be helpful on the city challenge

Your main objective is to guide a kiwibot to move autonomously from a food supply point to a delivery point. You are free to choose any method you want, but you are scored on the autopilot mode, and you should be able to provide an environment for us to test.

**Please play with the menu provided in the game, it can give you an overview of all the settings that are customizable**

## Score Calculation

A simple is score is calculated as follows:
```
float k1 = minDistance / (float)(Mathf.Max(minDistance,(robotDistance + pilotDistance)));
       float k2 = Mathf.Sqrt(Mathf.Max( 1, pilotDistance));
       int score = (int)(((MAXSCORE * k1) / k2) - (crash * 60));
```
On which `minDistance` is the shortest distance between the food supply and the provided delivery point. `pilotDistance` is the distance traveled while on AutoPilot mode, and `robotDistance` is the distance traveled while on manual mode. `crash` is the number of crashes while playing the game.

Observe that is not a requirement to do the whole circuit in autopilot, but you are severely penalized for spending any time on manual mode. As an observation: After one meter driven in manual, the final score reduces drastically.

### Available Game Builds (compiled builds of the simulator)

Instructions: Download the zip file, extract it and run (see How to Run) the execution file.

Version release: 6/21/17
### [Linux](https://github.com/Davidnet/kiwix/releases/download/v1.0/Linuxuniversal-kiwicampus-challenge.zip)

### [Mac](https://github.com/Davidnet/kiwix/releases/download/v1.0/Macuniversal-kiwicampus-challenge.zip)

### [Windows](https://github.com/Davidnet/kiwix/releases/download/v1.0/Windows64-kiwicampus-challenge.zip)

### **Releases on** [Link](https://github.com/Davidnet/kiwix/releases)

### How to run

#### Linux

In [Linux](https://github.com/Davidnet/kiwix/releases/download/v1.0/Linuxuniversal-kiwicampus-challenge.zip) the zip file contains two [ELF files](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format) that for security reasons are not marked to be executable. To give a file a executable flag the procedure is

```bash
$ chmod a+x file
```
A short summary of `chmod` can be found on the man pages using `man chmod` or on the [web](https://explainshell.com/explain?cmd=chmod+a%2Bx+file).
Be sure to choose the corresponding architecture of your OS.

| File   | Recommended Architecture |
| ----   |:------------------------:|
| x86    | 32 Bit OS                |
| x86-64 | 64 Bit OS                |

After giving the executable bits to the file, recall that for executing the file, use
```bash
$ ./file
```


#### Mac

In [Mac](https://github.com/Davidnet/kiwix/releases/download/v1.0/Macuniversal-kiwicampus-challenge.zip) a single app package is provided, is independent of the architecture. Any problem, please submit a issue report to this repository.

#### Windows

In [Windows](https://github.com/Davidnet/kiwix/releases/download/v1.0/Windows64-kiwicampus-challenge.zip) only a 64 bit version is provided, if you are interested on a 32 build, please open an issue on the issue tracker.

### General Recommendations

Is recommendable that if you don't have a GPU available on your system, please run the unity executable on low settings.

### General Controls

A mapping of the keyboard can be found on the settings menu, you can even use any joystick provided you OS can support it.

You can use any joystick supported by your OS, in the keyboard the following controls are provided (standard wasd mapping):

| keyboard   | Action |
| ----   |:------------------------:|
| wasd  | Control motion             |
| Space  | Break                |
| ESC    | Open close main menu |
|  C     | Change camera |
|  R     | Start recording |
|  P     | Begin AutoPilot connection |

### AutoPilot Communication



As you can observe in the communication tab, you can select a port, IP address to send images at a customizable size.

We send the images on a hex string over a socket, the communication sends strings of hex values that needs to be converted to a byteArray object representing the image (see the server.py). Observation: Read until a colon is found. This signals the image size segment.

A server script **which is not a requirement to use** is provided to give you a sketch to work on and give you an overview of how the communication is done **[server.py](server.py)**

Requirements: [Pillow](http://pillow.readthedocs.io/en/4.2.x/)

A requirements.txt is provided.


### Sending commands to the kiwibot:

The program is accepting the following format (example in python provided):

```python
'{ "steering" : "%f", "throttle" : "%f" }' % (steering, throttle)
```

The possible values are on the range:

| Value   | Range |
| ----   |:------------------------:|
| Steering   |  {-1,1}                |
| throttle  | {-1,1}                |




# Conda Kiwi Enviroment

Conda is a package manager application that quickly installs, runs, and updates packages and their dependencies. Conda is also an environment manager application. A Conda environment is a directory that contains a specific collection of Conda packages


We suggest (not a requirement) to use the following Conda environments so you can start as soon as possible to build your own AutoPilot on python.

## Installation


See [Anaconda](https://www.continuum.io/downloads)

Be sure to add anaconda/bin to the PATH, either saying yes on the installation menu or adding to your profile file (e.g bash.rc, .profile ... etc).


### Anaconda Usage

We provide to you with Conda environments included with Tensorflow and OpenCV (which can be useful for the hardest level)

### Linux

```
$ conda env create -f kiwix_linux.yml
```
Main packages provided: Tensorflow with GPU support and OpenCV. These environment has also Jupyter (which can be useful for visualization and writing python code), and scipy which can be useful for writing basic models of machine learning algorithms.

### Mac

TBA

### Windows

TBA

### Recommendations

There are many tools and configurations that can be useful for developing the solution, examples includes:

[Keras](https://keras.io/)

[Caffe](http://caffe.berkeleyvision.org/)

May the force be with you


![Kiwibot](./KIWIBOT.png)

# Contributors


Project by: [Carlos Zubieta](https://www.linkedin.com/in/carlos-zubieta-52217875/), [Jason Oviedo](https://www.linkedin.com/in/jason-oviedo-46611914/), and [David Cardozo](https://www.linkedin.com/in/davidcardozo/).

Kiwi Campus 2017


# Copyright

 © Kiwi Campus 2017
