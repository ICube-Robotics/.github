# ethercat_driver_ros2

This project proposes:
1. The [ethercat_driver_ros2](https://github.com/ICube-Robotics/ethercat_driver_ros2  ) package: a generic framework to build hardware interfaces for integrating EtherCAT modules within ros2_control.
    - Direct link to the [documentation of the package](https://icube-robotics.github.io/ethercat_driver_ros2/).
3. a [library](https://github.com/ICube-Robotics/ethercat_driver_ros2_examples ) of configurations files and plugins for the ethercat_driver_ros2 framework corresponding to popular EtherCAT modules. Those files can be used as configuration entry points in your project. You just have to modify the state or command interface names to match the ones you use in your project. You can also use them as starting points to build your own hardware interface configuration files if you use generic ecSlaves or if you need to build your own slave plugin to be used with the ethercat_driver_ros2 package.