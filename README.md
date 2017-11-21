# dual_lasers_test
This is an example to show how to use "laserscan_multi_merger" with two laser scanners.

# Prepare
## Install ira_laser_tools
    $ cd ~catkin_ws/src
    $ git clone  https://github.com/iralabdisco/ira_laser_tools
    $ cd ..
    $ catkin_make
## Install this repo
    $ cd ~catkin_ws/src
    $ git clone https://github.com/wennycooper/dual_lasers_test.git
    $ cd ..
    $ catkin_make

# Run
    $ roslaunch dual_lasers_test rplidar1.launch
    $ roslaunch dual_lasers_test rplidar2.launch
    $ roslaunch dual_lasers_test add_static_tf.launch
    $ rosrun rviz rviz

