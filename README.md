# dual_lasers_test
This is an example to show how to use "laserscan_multi_merger" to merge laserscan topics into a single virtual laserscan topic.

![](https://github.com/wennycooper/dual_lasers_test/blob/master/virtual_laserscan.png)


# Prepare
## Install ira_laser_tools
    $ cd ~catkin_ws/src
    $ git clone  https://github.com/iralabdisco/ira_laser_tools
    // modify laserscan_multi_merger.launch
    
            <param name="destination_frame" value="/virtual_laser"/>  
            <param name="cloud_destination_topic" value="/merged_cloud"/>
            <param name="scan_destination_topic" value="/virtual_laser"/>
            <param name="laserscan_topics" value ="/laser1 /laser2" />
    
    // modify ira_laser_tools/cfg/laserscan_multi_merger.cfg
    gen.add("angle_min", double_t, 0, "Minimum angle of the output scan", -3.14, -3.14, 3.14)
    gen.add("angle_max", double_t, 0, "Maximum angle of the output scan", 3.14, -3.14, 3.14)
    gen.add("angle_increment", double_t, 0, "Angle increment of the output scan", 0.008727, 0, 3.14)
    gen.add("time_increment", double_t, 0, "Time increment of the output scan", 0.0, 0, 1)
    gen.add("scan_time", double_t, 0, "Scan time of the output scan", 0.033333333, 0, 1)
    gen.add("range_min", double_t, 0, "Range min of the output scan", 0.1, 0, 50)
    gen.add("range_max", double_t, 0, "Range max of the output scan", 16.0, 0, 50)
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
    $ roslaunch dual_lasers_test add_static_tf.launch  // on terminal 3, it generates tf between virtual_laser, laser1 and laser2 
    $ roslaunch ira_laser_tools laserscan_multi_merger.launch  // on terminal 4  
    $ rosrun rviz rviz   // on terminal 5

