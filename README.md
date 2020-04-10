# BagFromImages

ROS package to generate a rosbag from a collection of images. Images are ordered alphabetically. The timestamp for each image is assigned according to the specified frequency. 

The bag will publish the images to topic `/camera/image_raw`.

Tested in ROS Fuerte.

## Installation on Ubuntu 16.04 kinetic
An excerpt from a nice intruction by Cartucho with a bit additional commands
https://github.com/raulmur/BagFromImages/issues/1#issuecomment-525041608

I tested the following commands on Ubuntu 16.04.6 LTS Xenial Xerus

Similarly I did the following:

    mkdir ~/ws_temp
    rosws init ~/ws_temp /opt/ros/kinetic/
    cd ws_temp/
    git clone https://github.com/raulmur/BagFromImages.git
    rosws set BagFromImages -t .
    cd BagFromImages/
    add the following line: target_link_libraries (${PROJECT_NAME} console_bridge) in the end of the file BagFromImages/CMakeLists.txt (keep the OpenCV as is).
    mkdir build
    cd build
    export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:~/ws_temp/BagFromImages
    sudo rosdep init
    rosdep update
    cmake ..
    make

When using the code, remember to run the following command again:

export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:~/ws_temp/BagFromImages

alternatively you can permanently add it to the .bashrc.

## Usage:

    rosrun BagFromImages BagFromImages PATH_TO_IMAGES IMAGE_EXTENSION FREQUENCY PATH_TO_OUPUT_BAG
  
 - `PATH_TO_IMAGES`: Path to the folder with the images
 - `IMAGE_EXTENSION`: .jpg, .png, etc. write the dot "."
 - `FREQUENCY`: Frames per second.
 - `PATH_TO_OUTPUT_BAG`: Path to save the bag (including the filename e.g. directory/filename.bag)

