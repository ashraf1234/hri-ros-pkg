# 1. Stack Summary #
"TurtleBot-HRI" is a specialized ROS stack developed at AASS Research Center, Örebro Universitet, Sweden that provides HRI tools for the TurtleBot. It provides apps like Static Hand-Gesture recognition using Kinect, Gesture control of robot navigation etc.
  * Authors: Prasanna Kumar and Chittaranjan S Srinivas.
  * Licence: GPL
**NOTE: The current version of the stack is usable but contains few bugs and it is being re-factored and more apps are being added at the moment.**

# 2. Packages #
## 2.1 key\_based\_navigation ##
key\_based\_nav controls the navigation of the TurtleBot in a known map where each room is represented by point and key associated with it. Given the key the TurtleBot moves through various 'way points' to reach the goal. (A sample map with 4 rooms, the goal points and way points can be found in goalpoints.inputfile).
### 2.1.1 Nodes ###
#### 2.1.1.1 key\_based\_nav ####
Code for navigation of single TurtleBot. Sends the TurtleBot to different locations that carry a label mentioned in goalpoints.inputfile
##### Published Topics #####
nav\_status, move\_base/cancel and move\_base/goal,
##### Subscribed Topics #####
room\_key, current\_pose and abort\_signal
#### 2.1.1.2 current\_pose\_publisher ####
Retrieves the current pose of the robot w.r.t. \world frame.
##### Published Topics #####
current\_pose


<p align='center'><img src='https://sites.google.com/site/prasannaportfolio/projects/plannerproj/nav_al.jpeg' align='center' height='400' width='550' /></p>
## 2.2 kinect\_gesture\_recognition ##
Reads a human gesture and associates the gesture to a key. The app read\_pose has 5 pre-programmed poses (up, down, there, here and nothing), checks if the input gesture is one among them and sends the key corresponding to the gesture to the topic room\_key.
### 2.2.1 Nodes ###
#### 2.2.1.1 openni\_tracker\_mod ####
Original openni\_tracker modified slightly to suit the app.
##### Published Topics #####
lost\_user\_num, new\_user\_num
#### 2.2.1.2 read\_user\_pose ####
Once recognized through psi pose. It reads the human's gesture (made by right hand) and attaches a key to it.
##### Published Topics #####
room\_key
##### Subscribed Topics #####
lost\_user\_num, new\_user\_num
## 2.3 robot\_hri ##
Contains apps like approaching the nearest human, behaviors for robot\_human hand-overs, robot get ready etc.. As such they do not make any sense but when put together they can be used for a purpose. These have been used in [HRI '13 paper "Robot-Human Hand-Overs in Non-Anthropomorphic Robots"](https://docs.google.com/file/d/0B-gg_jEjPWZtRVBUTUJ3Z1JmbkE/edit).

<p align='center'> <a href='http://www.youtube.com/watch?feature=player_embedded&v=c5CxlYl9YV8' target='_blank'><img src='http://img.youtube.com/vi/c5CxlYl9YV8/0.jpg' width='425' height=344 /></a> </p>

