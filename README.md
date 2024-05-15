# JetsonNano-ROS2
A comprehensive guide on setting up JetsonNano with ROS2

## Setup

- Jetson Nano can be generally powered from a micro usb power supply (5V 2A 10W max). This can manage a keyboard, a mouse and a small camera.
- If planned use case for Jetson Nano is to run Neural Networks along with Depth cameras, it is better to power the device via the DC barrel jack (5V 4A 20W max).

<br>

## System setup comparision

| Base OS | Jetpack | ROS | Dockerized | Desktop | CPU & GPU overclocked | Idle RAM usage | Storage | Tutorial |
|---	|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Ubuntu 20.04 [QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Humble | Yes	| Yes | CPU 1900Mz & GPU 950Mz |     |     |     |
| Ubuntu 20.04	[QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Humble	| Yes | No |  CPU 1900Mz & GPU 950Mz |     |     |     |
| Ubuntu 20.04 [QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Foxy | No | Yes	| CPU 1900Mz & GPU 950Mz | 1.5 GB [image](/JetsonNano-ROS2/images/330652618-93d043ec-4f78-4a03-b43a-d95c21a98f6d.png) | 14.9 GB | Link |
| Ubuntu 20.04	[QEngineering](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) | 4.6.1 | Foxy | No	| No 	| CPU 1900Mz & GPU 950Mz |     |     |     |
| Ubuntu 18.04 [Jetson Linux](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | Humble 	| Yes | Yes | CPU 1479Mz & GPU 920Mz |     |     |     |
| Ubuntu 18.04 [Jetson Linux](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write)| 4.6.4 | Humble	| Yes | No | CPU 1479Mz & GPU 920Mz |     |     |     |


## Ubuntu Installation

1. Follow the instructions [here](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) to download the bare Ubuntu 20.04 image for Jetson Nano.
2. Boot the SD card using the downloaded image and [balenaEtcher](https://etcher.balena.io/).
3. Insert the SD card to Jetson Nano and bootup the device. If prompted, username is 'jetson' and and password is 'jetson'.
4. Login to the system and run following commands to update the system.
   ```bash
   sudo apt update
   ```
   and
   ```bash
   sudo apt upgrade
   ```

## ROS Installation

1. Install ROS 2 Foxy ROS Base (Bare Bones Installation) following instructions [here](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)
