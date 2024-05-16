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
5. Add CUDA path to .bashrc. First open .bashrc 
   ```bash
   gedit .bashrc
   ```
   and add the following lines to end of the file
   ```bash
   export PATH=${PATH}:/usr/local/cuda/bin
   export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda/lib64
   ```


<br>

## Testing the CUDA functionality

1. Open a new Terminal to refresh the path variables. Then run,

   ```bash
   /usr/local/cuda-10.2/bin/cuda-install-samples-10.2.sh .
   cd NVIDIA_CUDA-10.2_Samples/
   ```

2. Build the examples by running
   ```bash
   make
   ```

   if an error pops up saying,

   ```bash
   error -- unsupported GNU version! gcc versions later than 8 are not supported!
   ```
   run

   ```bash
   make HOST_COMPILER=/usr/bin/g++-7
   ```

<br>

## ROS Installation

1. Install ROS 2 Foxy ROS Base (Bare Bones Installation) following instructions [here](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)

2. Then in the terminal run,

   ```bash
   echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
   ```