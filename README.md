## ELEC5660 Introduction to Aerial Robotics: Project 1 Phase 2

In phase 1, a controller is implemented and the quadrotor can track a pre-defined trajectory. Phase 2 will focus
on trajectory generator. A carefully designed path planner can enable the quadrotor to operate aggressively and
precisely. Your task includes:

### Trajectory Generator
A natural way to command the quadrotor is to set waypoints that it needs to pass by. What the path planner
needs to do is to generate a trajectory that:
- connects all waypoints (including start and goal points).

- meets smoothness criterion.

Two sets of waypoints are provided in [test_trajectory.m](/L4-%20Time%20%26%20Motion%20Trajectory%20Generation/proj1phase2/code/test_trajectory.m). You need to design two more sets of waypoints
(with at least 6 waypoints). You can choose either 5th order polynomial trajectory or minimum snap trajectory [1].
The later one is our recommendation and will win you bonus points.

### Tutorial
You can use the naive trajectory generation method in your lecture (only smoothness and connection of waypoints is required), or you can try the optimization-based method (We encourage you generate the trajectory using
this method). If you prefer the latter one, you have two ways to implement it:
- You can use the method in the slides of [Lecture4](/L4-%20Time%20%26%20Motion%20Trajectory%20Generation/L4.pdf) to map the original constrained quadratic program (QP) to
an unconstrained QP, and then obtain the closed form solution of the unconstrained QP directly.
- You can use [quadprog](https://www.mathworks.com/help/optim/ug/quadprog.html) function in Matlab to solve the constrained QP. This function is originated in Matlab,
and you can type in “help quadprog” in the command window for more detail.

### Sturcture of the Simulator

The simulation code is almost the same with [proj1phase1](/L3-%20Control%20Basics%20Quadrotor%20Control/proj1phase1/) but a [trajectory_generator.m](/L4-%20Time%20%26%20Motion%20Trajectory%20Generation/proj1phase2/code/test_trajectory.m) as the main entry point.

```bash
+ code
  + readonly #supposed to be read only
    - quadModel_readonly.m #parameters of a 500g quadrotor
    - quadEOM_readonly.m #dynamics model of quadrotor.
    - run_trajectory_readonly.m #solve the equation of motion, receive desired trajectory,run your controller, iteratively. visualization is also included.
  + utils #useful functions.
  - controller.m #You have alredy had a good controller in proj1phase1
  - trajectory_generator.m #What you need to work with. Design the trajectory for quadrotor given the path. And calculate desired state given current time.
  - test_trajectory.m #main entry.
```

[1]: D. Mellinger and V. Kumar, “Minimum snap trajectory generation and control for quadrotors,” in Proc. of the IEEE Int. Conf. on Robotics and Automation, Shanghai, China, May 2011.
