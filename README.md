# JetsonNano-ROS2
A comprehensive guide on setting up JetsonNano with ROS2

## Setup

- Jetson Nano can be generally powered from a micro usb power supply (5V 2A 10W max). This can manage a keyboard, a mouse and a small camera.
- If planned use case for Jetson Nano is to run Neural Networks along with Depth cameras, it is better to power the device via the DC barrel jack (5V 4A 20W max).

<br>

## System setup comparision

| Ubuntu | Jetpack | CUDA | ROS | GUI | Docker | CPU / GPU Frequency | Idle RAM (GB) | Storage (GB)| Tutorial |
|---	|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2 |Humble | Yes	| Yes | 1900Mz / 900Mz |     |     |     |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Humble	| No | Yes | 1900Mz / 900Mz |     |     |     |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Foxy | Yes | No | 1900Mz / 900Mz | 1.5 / 3.9 | 14.9 | [Image](/JetsonNano-ROS2/images/u20-foxy-noDocker-Desktop.png) [Tutorial](/JetsonNano-ROS2/docs/u20-foxy-noDocker-Desktop.md) |
| [20.04](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.2 | 10.2  |Foxy | No	| No 	| 1900Mz / 900Mz | 0.5 / 3.9 |     | [Image](/JetsonNano-ROS2/images/u20-foxy-noDocker-noDesktop.png) [Tutorial](/JetsonNano-ROS2/docs/u20-foxy-noDocker-noDesktop.md) |
| [18.04](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | 10.2  | Humble | Yes | Yes | 1479Mz / 920Mz |     |     |     |
| [18.04](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | 10.2  | Humble	| No | Yes | 1479Mz / 920Mz |     |     |     |