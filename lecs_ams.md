**[Home](https://AbLECPS.github.io) >> LECs and AMs**

# LECs and AMs

In this release there are 3 LECs (neural networks) with AMs (assurance monitors). LECs are using TensorFlow 2.6.2 Lite (GPU, but can run with TF-CPU). LEC2 & LEC3 can run on Google Coral accelerator. Assurance Monitors run on PyTorch (CPU or CUDA GPU).

* LEC2Lite with VAE AM:
  * This is a segmentation LEC for the VU SSS images (pipe perception). 
  * AM is a VAE. LEC and AM were trained on SIM and HW collected data. HW version is using a Rover with an RpLidar as the side scan source. When log(Martingale) value is high, pipe estimation is disabled. If the mission is pipe mapping BT also commands UUV for minimum speed to improve scan quality
  * LEC is implemented in TF2.6.2 Lite, can run on CUDA GPU, CPU or Google Coral accelerator.
  * [Sources for LEC2](https://github.com/AbLECPS/alc/tree/main/bluerov2_standalone/catkin_ws/src/lec2lite)
  * Trained AM and AM training activity can be found in the Toolchain
* LEC3Lite with VAE AM: 
  * This is a signal processing NN. Input is the 252 bin FLS raw data (simulated signal from Gazebo or digitalized signal from MaxBotix sonar - with multiple contact echos)
  * The lec node will return with an array of contacts in [m]
  * TFLite inference takes around 2ms in average on x64 CPU (i7-9900)
  * Trained with SIM and HW data (MaxSonar MB7070 using Analog Envelope output + RPi Pico)
  * LEC is implemented in TF2.6.2 Lite, can run on CUDA GPU, CPU or Google Coral accelerator.
  * [Sources for LEC3](https://github.com/AbLECPS/alc/tree/main/bluerov2_standalone/catkin_ws/src/lec3lite)
  * Trained AM and AM training activsity can be found in the Toolchain
* FDIR integrated with Selective Classification AM:
  * FDIR system has a thruster degradation / fault detection LEC combined with Selective Classification assurance monitor, and a Behaviour Tree based control reallocation logic. More details can be found in the MDPI paper linked above.
  * Trained LEC & AM and training activity can be found in the Toolchain

