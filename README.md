# RustBot
Software tools for the project Sistemas Embarcados de Vistoria (SEV). We refer to the hardware platform as RustBot because the AVT Mako cameras look kind of rusty (sorry for the lack of creativity).

## Table of Contents

* [The Robot](#therobot)
* [Installation](#installation)
* [Usage](#usage)
* [Finding IP Address of Cameras](#findingcameraip)
* [Calibration](#calibration)
* [Calibration Setup](#calibrationsetup)

## <a name="therobot"></a>The Robot

The RustyBot is a stereo vision system with two AVT Mako cameras mounted on a plate. The baseline is around 0.1 meters, and the cameras are horizontally aligned. Here's a picture of the system

![robot](https://github.com/miguelriemoliveira/RustBot/blob/master/docs/robot.jpg)

## <a name="installation"></a>Installation

First, the Vimba sdk must be downloaded and compiled. We will refer to the folder where the sdk is installed as **$(Vimba_2_0)**.

You may download this sdk from [https://www.alliedvision.com/en/products/software.html](https://www.alliedvision.com/en/products/software.html). Then follow the installation instructions in **$(Vimba_2_0)/Documentation/ReleaseNotes.txt** to install the sdk.

After that, the ros vimba wrapper at [http://wiki.ros.org/avt_vimba_camera](http://wiki.ros.org/avt_vimba_camera) should work. So install the ros wrapper

```bash
git clone https://github.com/srv/avt_vimba_camera.git
catkin_make
```

## <a name="usage"></a>Usage

To launch a single camera use

```bash
roslaunch rustbot_bringup left_camera.launch
```

## <a name="findingcameraip"></a>Finding IP Address of Cameras

To find out the ip address and the id of your cameras. From the **$(VimbaPath)/examples/ListCamera** folder, run

```bash
cd $(Vimba_2_0)
/Tools/Viewer/Bin/x86_64bit/VimbaViewer
```

You shoud see the VimbaViewer gui with all connected cameras with their id (guid). 

![vimba_viewer](https://github.com/miguelriemoliveira/RustBot/blob/master/docs/vimba_viewer.png)

Select a camera and then, on the right side pane, select All propperties and search for "IP Address" to find out the the ip address.

![get_ipaddress](https://github.com/miguelriemoliveira/RustBot/blob/master/docs/get_ipaddress.png)



You may edit the file **launch/mono_camera.launch** and 
 

By setting the correct guid and ip of your camera.

You can get the guid and ip of your camera by using the ListCamera or VimbaViewer binaries in

Vimba_2_0/VimbaCPP/Examples/Bin/x86_64bit
