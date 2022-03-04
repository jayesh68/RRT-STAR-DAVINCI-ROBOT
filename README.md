# Path planning for a dual arm Da Vinci Surgical robot using RRT*

## Steps to run the package
1. Clone the repository and move into the directory of the ROS package. 
2. Gazebo can be launched by running the command roslaunch davinci_final control_gazebo.launch
3. The python script can be run using the command python3 sample_controller.py

## DaVinci Robot in Gazebo
<img src="https://github.com/jayesh68/RRT-DAVINCI-SURGICAL-ROBOT-/blob/main/Screenshot%20from%202022-03-04%2011-45-48.png"/>

## Algorithm
1. Firstly a CAD model of the daVinci robot is designed using Solidworks. The model is converted into a URDF format and importedto ROS, Gazebo and RVIZ to publish values to the different joints. 
2. The code for the RRT* algorithm is implemented by considering the joint limits of the two arms. A linearly uniform random set of joint angles are chosen and forward kinematics is performed to find out the end effector position. The end effector position is in turn verified by computing the joint angles and checking if it lies within the joint limits and is within the reachable workspace. This makes sure that the point is a valid state and if such, the node
is added to the tree. 
3. Once added the cost of its neighbors are computed and compared with the random point chosen and the node with the lowest cost from this set is chosen as
the new node. The tree is then rewired. 
4. As new nodes are continuously added to the tree, the cost with respect to the goal is checked to ensure that the tree is expanding towards the goal thus generating the optimal trajectory. 
5. The validation of this algorithm includes testing if the two arms can reach different goal states by avoiding collisions with the obstacles and with each other and also to perform a handoff operation where the arm containing the needle can be moved towards the gripper arm allowing the gripper arm to grasp the object. 

## Simulation Videos
https://youtu.be/cARsSiiyXLY
