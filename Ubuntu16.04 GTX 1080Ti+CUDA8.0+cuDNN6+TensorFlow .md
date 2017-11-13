### Install Ubuntu16.04 LTS version ###
### Install CUDA8.0 and cuDNN6 ###
Thanks for this link: https://github.com/nicolaifsf/Installing-Tensorflow-with-GPU

1. Download CUDA Tookit8.0 runfile (local) https://developer.nvidia.com/cuda-80-ga2-download-archive

![CUDA Tookit8.0](http://upload-images.jianshu.io/upload_images/1868025-7e0b84a51c2efae9.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/480)

2. Download CUDNN from https://developer.nvidia.com/cudnn

<div align=center>
![cuDNN download](http://upload-images.jianshu.io/upload_images/1868025-6a41218b9534589c.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/480)

3. Download GTX1080Ti driver from http://www.nvidia.com/Download/index.aspx

![GTX1080Ti driver](http://upload-images.jianshu.io/upload_images/1868025-6589de52abd79623.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/480)

4. Run: 
```
$ sudo apt-get install build-essential
```
5. Create the */etc/modprobe.d/blacklist-nouveau.conf* file with 
```
$ sudo vim /etc/modprobe.d/blacklist-nouveau.conf
```
    In *blacklist-nouveau.conf*， input (you may need to install **vim** first)
```
blacklist nouveau
options nouveau modeset=0
```
    Then,
```
$ sudo update-initramfs -u
```
6. Reboot your computer
```
$ reboot
```
7. On login screen, press **ctrl + alt + f1** to open up login as tty1. You need to input your name and password in this step.
8. Navigate to the folder where you downloaded the files from steps 1, 2 and 3. 
9. Run:
```
$ chmod +x cuda_8.0.61_375.26_linux.run
$ chmod +x NVIDIA-Linux-x86_64-378.13.run
$ sudo service lightdm stop
$ sudo apt-get remove --purge nvidia-*
```
10. Run:
```
$ sudo ./NVIDIA-Linux-x86_64-378.13.run --no-opengl-files
```
    Just continue through the installation **UNTILL IT ASKS YOU** 'Would you like to run the nvidia-xconfig utility...' Hit **NO** for this step.
11. Run:
```
$ sudo ./cuda_8.0.61_375.26_linux.run --no-opengl-libs
```
    Following the options below
```
Accept the EULA
No to Install NVIDIA Accelerated Graphics Driver for Linux-x86_64
Yes to Install the CUDA 8.0 Toolkit
Enter toolkit location to be  (default): /usr/local/cuda-8.0
Yes to install a symbolic link at /usr/local/cuda
Yes to install the CUDA 8.0 Samples
Default location for CUDA Samples location (or wherever you want them)
```
12. Run:
```
$ sudo modprobe nvidia
```
13. Set Environment path variables (add to *.bashrc*):
```
$ sudo vim ~/.bashrc
```
In the end of *.bashrc*, add
```
export PATH=/usr/local/cuda-8.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH
```
14. Run:
```
$ source ~/.bashrc
$ cat /proc/driver/nvidia/version
$ nvcc -V
$ sudo service lightdm start
```
15. Navigate to the CUDA samples we installed in step 11, then run: 
```
$ make -j8
```
16. Navigate to: *NVIDIA_CUDA-8.0_Samples/bin/x86_64/linux/release/* for the tests and run:
```
$ ./deviceQuery
$ ./deviceQuery
```
17. Reboot your computer
```
$ reboot
```
18. After rebooting, navigate to the folder where you downloaded the files from steps 1, 2 and 3 and run:
```
$ tar -xzvf cudnn-8.0-linux-x64-v6.0.tgz
$ sudo cp cuda/lib64/* /usr/local/cuda/lib64/
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
```
19. Run:
```
$ sudo apt-get install libcupti-dev
```
Congratualations! All CUDA dependencies for Tensorflow should now be installed.
### Install TensorFlow r1.4 ###
I used **"native" pip** method https://www.tensorflow.org/install/install_linux#InstallingNativePip and the python version is python3.5.

