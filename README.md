# dual_lasers_test
This is an example to show how to use "laserscan_multi_merger" to merge laserscan topics into a single virtual laserscan topic.

![](https://github.com/wennycooper/dual_lasers_test/blob/master/virtual_laserscan.png)


# Prepare
## Install ira_laser_tools
    $ cd ~catkin_ws/src
    $ git clone  https://github.com/iralabdisco/ira_laser_tools
    // modify laserscan_multi_merger.launch
    // modify ira_laser_tools/cfg/laserscan_multi_merger.cfg
    $ cd ..
    $ catkin_make
    // Note that if you modify laserscan_multi_merger.cfg, you need to make it again
    
## Install this repo
    $ cd ~catkin_ws/src
    $ git clone https://github.com/wennycooper/dual_lasers_test.git
    $ cd ..
    $ catkin_make

# Run
    $ sudo chmod 666 /dev/ttyUSB[01]
    $ roslaunch dual_lasers_test rplidar1.launch  // on terminal 1
    $ roslaunch dual_lasers_test rplidar2.launch  // on terminal 2
    $ roslaunch dual_lasers_test add_static_tf.launch  // on terminal 3
    $ roslaunch ira_laser_tools laserscan_multi_merger.launch  // on terminal 4  
    $ rosrun rviz rviz   // on terminal 5

