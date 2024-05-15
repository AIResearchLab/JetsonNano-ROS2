# JetsonNano-ROS2
A comprehensive guide on setting up JetsonNano with ROS2

## Setup

- Jetson Nano can be generally powered from a micro usb power supply (5V 2A 10W max). This can manage a keyboard, a mouse and a small camera.
- If planned use case for Jetson Nano is to run Neural Networks along with Depth cameras, it is better to power the device via the DC barrel jack (5V 4A 20W max).

<br>

## System setup comparision

| Base OS | Jetpack | ROS | Dockerized | Desktop | CPU / GPU Frequency | Idle RAM (GB) | Storage (GB)| Tutorial |
|---	|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Ubuntu 20.04 [QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Humble | Yes	| Yes | 1900Mz / 950Mz |     |     |     |
| Ubuntu 20.04	[QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Humble	| Yes | No |  1900Mz / 950Mz |     |     |     |
| Ubuntu 20.04 [QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Foxy | No | Yes	| 1900Mz / 950Mz | 1.5 / 3.9 | 14.9 | [Image](/JetsonNano-ROS2/images/u20-foxy-noDocker-Desktop.png) [Tutorial](/JetsonNano-ROS2/docs/u20-foxy-noDocker-Desktop.md) |
| Ubuntu 20.04	[QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Foxy | No	| No 	| 1900Mz / 950Mz | 0.5 / 3.9 |     | [Image](/JetsonNano-ROS2/images/u20-foxy-noDocker-noDesktop.png) [Tutorial](/JetsonNano-ROS2/docs/u20-foxy-noDocker-noDesktop.md) |
| Ubuntu 18.04 [Jetson Linux](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | Humble 	| Yes | Yes | 1479Mz / 920Mz |     |     |     |
| Ubuntu 18.04 [Jetson Linux](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | Humble	| Yes | No | 1479Mz / 920Mz |     |     |     |