 Mobile Manipulator Pick-and-Place (CoppeliaSim)

**Objective**
Implement a control pipeline for a mobile manipulator to execute a precise pick-and-place task with smooth motion and stable tracking.

**Approach**

* **Trajectory Generation**

  * 8-segment end-effector trajectory (initial, standoff, grasp, transfer, release)
  * Cartesian / screw interpolation with quintic time-scaling
  * Includes gripper state (open/close) and dense reference waypoints

* **Kinematics Simulation (NextState)**

  * First-order Euler integration for state update
  * Updates chassis, arm joints, and wheels from control inputs
  * Enforces velocity limits to keep motion physically feasible

* **Feedback Control (FeedbackControl)**

  * Feedforward + PI control for trajectory tracking
  * Computes configuration error (pose error in SE(3))
  * Uses Jacobian pseudoinverse to map desired twist → joint & wheel velocities

**Outcome**
Accurate trajectory tracking with stable control, enabling reliable pick-and-place execution in simulation.
