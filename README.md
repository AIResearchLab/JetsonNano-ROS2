# JetsonNano-ROS2
A comprehensive guide on setting up JetsonNano with ROS2

## Setup

- Jetson Nano can be generally powered from a micro usb power supply (5V 2A 10W max). This can manage a keyboard, a mouse and a small camera.
- If planned use case for Jetson Nano is to run Neural Networks along with Depth cameras, it is better to power the device via the DC barrel jack (5V 4A 20W max).

- System setup comparison section contains various combinations of Ubuntu and ROS2 that was tested with and without GUI, and with and without docker.

- Main purpose was to identify the stable combination that allows for the latest ROS version to be used as well as get the maximum output from the Jetson Nano

<br>

## System setup comparision

- GUI column represents whether a GUI is available or not. No GUI was achieved by removing all the GUI related components. Please refer relevant tutorials for the steps.

- Idle RAM has been measured as it determines the Neural Netork model sizes that can be loaded into the device. 

- In the combinations that has Docker, the Idle RAM has been measured while the Base ROS Docker image is running.

- Only the provided overclocking settings was used, but further customization can be done according to [here](https://qengineering.eu/overclocking-the-jetson-nano.html)


| Ubuntu | Jetpack | CUDA | ROS | GUI | Docker | CPU / GPU Frequency | Idle RAM (GB) | Tutorial |
|---	|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2 |Humble | Yes	| Yes | 1900Mz / 998Mz |     |     |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Humble	| No | Yes | 1900Mz / 998Mz |     |     |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Foxy | Yes | No | 1900Mz / 998Mz | 1.5 / 3.9 | [Image](/images/u20-foxy-noDocker-Desktop.png) [Tutorial](/docs/u20-foxy-noDocker-Desktop.md) |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Foxy | No	| No 	| 1900Mz / 998Mz | 0.4 / 3.9 | [Image](/images/u20-foxy-noDocker-noDesktop.png) [Tutorial](/docs/u20-foxy-noDocker-noDesktop.md) |
| [18.04](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | 10.2  | Humble | Yes | Yes | 1479Mz / 920Mz | 0.4 / 3.9 | [Image](/images/u18-humble-Docker-Desktop.png) [Tutorial](/docs/u18-humble-Docker-Desktop.md) |
| [18.04](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | 10.2  | Humble	| No | Yes | 1479Mz / 920Mz |     |     |