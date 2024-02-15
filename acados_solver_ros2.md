# acados_driver_ros2

This project includes:
1. The [acados_vendor_ros2](https://github.com/ICube-Robotics/acados_vendor_ros2) package: a vendored package for the Acados optimization framework that exposes both the C library and the Python library (`acados_template` python module).
2. The [acados_solver_ros2](https://github.com/ICube-Robotics/acados_solver_ros2) repos that contains the helper packages to build Acados solver plugins for NMPC: `acados_solver_base` and `acados_solver_plugins`. The repos also contains the general [documention](https://icube-robotics.github.io/acados_solver_ros2/) for the Acados stack:
3. The [acados_solver_ros2_examples](https://github.com/ICube-Robotics/acados_solver_ros2_examples) repos that contains demo packages to use `acados_solver_ros2` to control a robot. The application includes an Acados-based plugin for NMPC, a ros2-control controller that uses the plugin, and a simulation setup with an inverted pendulum.