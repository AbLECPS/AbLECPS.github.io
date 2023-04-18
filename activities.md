
**[Home](https://AbLECPS.github.io) >> Challenge Problems**

# Challenge Problems - BlueROVSim Activity

Challenge problem (CP) examples are available from the ALC Toolchain both in headless mode (running as an activity) and using IDE (running from command line). Examples in this release includes the following:

### CP1 Pipe tracking
UUV has to follow an underwater pipe on the seabed using side scanning sonar and perception LEC. During mission various hazards (obstacles) and failsafes (battery low, geofence etc.) can occur.
### CP2 Thruster degradation
This challenge problem is based on CP1, with thruster degradations. FDIR system detects and mitigates the problem.
### CP4 Waypoint Following
This is a waypoing following mission type, with the same hazards and failsafes as in CP1.
### Real-Time Reachability
The real-time reachability involves running the reachability analysis code at run-time (with the simulation) and compute the
reachability of UUV to check if there will be a collision in projected window. RtReach node is always running in the BlueROV simulation. It warns the behavior tree if the commanded heading leads to an unsafe situation for the uuv (collision with obstacle or nogo zone). When RtReach reports UNSAFE condition based on the obstacles, the UUV is commanded to  "emergency stop". Thereafter the UUV moves straight up to the surface.

The available examples in this release can be found in ALC/Construction/Testing/ when using Activities or $ALC_HOME/bluerov2_standalone/catkin_ws/src/vandy_bluerov/scripts/ when using command line. To execute these examples please follow the steps described in the documentation and in the front page videos.

## Using BlueROVSim Activity

- To create  a new instance of the BlueROVSim activity, open a BlueROVActivity  model and switch to ALC/Construction/ and click on Testing or DataCollection model.
- Then Drag and drop the "Activity" model from the Part Browser on the left.
- Inside the "Activity" model, launch the "ActivityInit" plugin  (Sometimes this plugin throws an error with a red-box message. Please ignore this and re-run this plugin.)
- Once this plugin is running, in the initial dialog box choose the "bluerov_sim" activity.
- In the subsequent dialog box, choose one or more options that can be configured as part of the BlueROV simulation. Options include 
   - Waypoint: Setting up random waypoint generation.
   - Pipeline: Setting up pipeline generation for tracking pipeline.
   - Obstacle:  Static and dynamic obstacle generation during simulation.
   - Degradation: Configuring the thruster degradation and FDIR
   - AIS: This is for setting up the AIS simulation. This feature will be supported in the next release which will include a planner as part of the BlueROV autonomy stack.
   - NoGoZone: Configure the no-go zone.
- Once the options are choosen and submitted, this generates an activity model for simulation.
- The user may change the defaut parameters associated with each of the options above and run the simulation by using the launch activity plugin (refer to headless video).
- When the user hovers over a parameter, its description is shown.
- A list of important parameters to tweak for the CP1, CP2, and CP4 scenarios is presented below.

## Common parameters across all scenarios

- The parameters in "Execution" table are common across all scenarios. The user may 
   tweak the following parameters
    - timeout (simulation execution time)
    - random_val (random seed for simulation)
