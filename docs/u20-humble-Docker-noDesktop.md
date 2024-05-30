## Ubuntu Installation

1. Follow the instructions [here](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image?tab=readme-ov-file#bare-image) to download the bare Ubuntu 20.04 image for Jetson Nano.
2. Boot the SD card using the downloaded image and [balenaEtcher](https://etcher.balena.io/).
3. Insert the SD card to Jetson Nano and bootup the device. If prompted, username is 'jetson' and password is 'jetson'.
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

6. Temporary disabling the GUI via Ctrl+Alt+F7 [does not free up the RAM](/images/u20-GUI-temporary-disable-terminal.png). Temporory disabling the GUI environment via GRUB did not succeed as there is no grub in arm architecture and could not figure out how to modify the boot parameters. Leaving for future....

7. Remove Desktop environment, Display manager, Libreoffice and other GUI based stuff based on [Issue 88](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/issues/88)

   ```bash
   sudo chown root:root / /lib
   sudo apt purge ubuntu-desktop -y && sudo apt autoremove -y && sudo apt autoclean
   sudo apt-get remove nautilus nautilus-* gnome-power-manager gnome-screensaver gnome-termina* gnome-pane* 
   sudo apt-get remove gnome-applet* gnome-bluetooth gnome-desktop* gnome-sessio* gnome-user* gnome-shell-common
   sudo apt-get remove zeitgeist-core libzeitgeist* gnome-control-center gnome-screenshot && sudo apt-get autoremove
   sudo apt-get remove --purge libreoffice*
   sudo apt-get remove libreoffice-core
   sudo apt-get remove snapd lightdm cups chromium*
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
3. Run the following command to test
   ```bash
   ./bin/aarch64/linux/release/deviceQuery
   ```
   and output should be similar to the following
   ```bash
   ./bin/aarch64/linux/release/deviceQuery Starting...

   CUDA Device Query (Runtime API) version (CUDART static linking)

   Detected 1 CUDA Capable device(s)

   Device 0: "NVIDIA Tegra X1"
   CUDA Driver Version / Runtime Version          10.2 / 10.2
   CUDA Capability Major/Minor version number:    5.3
   Total amount of global memory:                 3964 MBytes (4156399616 bytes)
   ( 1) Multiprocessors, (128) CUDA Cores/MP:     128 CUDA Cores
   GPU Max Clock rate:                            998 MHz (1.00 GHz)
   Memory Clock rate:                             13 Mhz
   Memory Bus Width:                              64-bit
   L2 Cache Size:                                 262144 bytes
   Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096)
   Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
   Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
   Total amount of constant memory:               65536 bytes
   Total amount of shared memory per block:       49152 bytes
   Total number of registers available per block: 32768
   Warp size:                                     32
   Maximum number of threads per multiprocessor:  2048
   Maximum number of threads per block:           1024
   Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
   Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
   Maximum memory pitch:                          2147483647 bytes
   Texture alignment:                             512 bytes
   Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
   Run time limit on kernels:                     Yes
   Integrated GPU sharing Host Memory:            Yes
   Support host page-locked memory mapping:       Yes
   Alignment requirement for Surfaces:            Yes
   Device has ECC support:                        Disabled
   Device supports Unified Addressing (UVA):      Yes
   Device supports Compute Preemption:            No
   Supports Cooperative Kernel Launch:            No
   Supports MultiDevice Co-op Kernel Launch:      No
   Device PCI Domain ID / Bus ID / location ID:   0 / 0 / 0
   Compute Mode:
      < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

   deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 10.2, CUDA Runtime Version = 10.2, NumDevs = 1
   Result = PASS
   ```
   
<br>

## ROS Installation

1. Start the ROS2 Humble ros-base docker container using the following command. For more customized containers checkout [KalanaRatnayake/Jetson-ROS-Docker](https://github.com/KalanaRatnayake/Jetson-ROS-Docker). To build your own docker images, follow instructions at [dusty-nv/jetson-containers](https://github.com/dusty-nv/jetson-containers)

   ```bash
   docker pull dustynv/ros:humble-ros-base-l4t-r32.7.1
   docker run --rm -it --runtime nvidia --network host --gpus all -e DISPLAY dustynv/ros:humble-ros-base-l4t-r32.7.1
   ```