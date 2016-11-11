# meccabrain
Jetson TX1 equipped meccanoid G15KS

## Documentation

### Setting up the Meccanoid
Assemble it according to the [instructions](http://cdn.meccano.com/notice/15402.pdf)

### Setting up the Jetson

#### Host
Start by register an account on the Nvidia [Embedded Developer Program](https://developer.nvidia.com/embedded-developer-program) to get access to software and documentation needed to set up the Jetson TX1.

Once you've got the account go to the [Embedded Download Center](https://developer.nvidia.com/embedded/downloads) and download the **JetPack for L4T** installer and install both host and target software / connect everything according to the provided installation guidelines. *We used JetPack 2.3 for which your host computer will need to run Ubuntu 14.04 (works using a virual machine) and your Jetson will be running 64-bit Ubuntu 16.04.*

#### Target
Once Ubuntu is booted up on the target we made a number of things as described below

##### External Storage
We used a 32GB SanDisk Ultra SDHC card. To enable executables from the SD card you will have to format it with the *Ext4* file system. Start by inserting the SD card in the socket on the development board (which should then be mounted) then open up a terminal and check the path of your device by running 
```
$ lsblk
``` 
You should probably see your device at `/dev/mmcblk1p1`. Now unmount the SD card (click the unmount button on the sd card icon) and then format by running
```
$ sudo mkfs.ext4 /dev/mmcblk1p1
```
given that your devices is located at `/dev/mmcblk1p1`. Finally change the ownership of the device to enable permissions by running
```
$ sudo chown ubuntu /media/ubuntu/name-of-your-device
```
if username is `ubuntu` (default) and your device is mounted at `/media/ubuntu/name-of-your-device`.

##### Installing some software

Starting with `git` by running
```
$ sudo apt-get update
$ sudo apt-get install git
```

then `lm-sensors` (if you want to monitor temperature etc.) by running 
```
$ sudo apt-get install lm-sensors
$ sudo sensors-detect
$ watch -n 1 sensors
``` 
We also decided to go with `ROS` (Robot Operating System) which is installed by running ... 


### Modifying the Meccanoid (replacing the Meccabrain)

#### Interfacing the smart modules using the Jetson
*TODO: GPIO... communication protocol... ROS package..*

#### Camera Module
*TODO: Existing ROS packages for e.g. kinect...*

#### Face authentication/recognition
*TODO: ROS package for dl-inference...*

## Resources

  * [The official Jetson TX1 wiki](http://elinux.org/Jetson_TX1)
  * [Jetsonhacks projects](http://www.jetsonhacks.com/)
