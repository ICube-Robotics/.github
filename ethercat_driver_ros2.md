# EtherCAT tools for ROS2

This project proposes:
1. The [ethercat_driver_ros2](https://github.com/ICube-Robotics/ethercat_driver_ros2  ) package: a generic framework to build hardware interfaces for integrating EtherCAT modules within ros2_control.
    - Direct link to the [documentation of the package](https://icube-robotics.github.io/ethercat_driver_ros2/).
2. a [library](https://github.com/ICube-Robotics/ethercat_driver_ros2_examples ) of configurations files and plugins for the ethercat_driver_ros2 framework corresponding to popular EtherCAT modules. Those files can be used as configuration entry points in your project. You just have to modify the state or command interface names to match the ones you use in your project. You can also use them as starting points to build your own hardware interface configuration files if you use generic ecSlaves or if you need to build your own slave plugin to be used with the ethercat_driver_ros2 package.
3. [ soem_vendor_ros2](https://github.com/ICube-Robotics/soem_vendor_ros2)   Vendored package for the Simple Open Source EtherCAT Master (SOEM) ethercat master library.
4. a dedicated [controller](https://github.com/ICube-Robotics/gpio_controllers) to monitor and control gpios from ROS2 topics. It interfaces naturally with GPIOs from EtherCAT slaves.


## Installation of igh with the debian packages

We offer 2 debian packages to help install the igh master:
1. [for x86-amd64 architectures](https://seafile.unistra.fr/f/7b38a17736d14a08a8ee/?dl=1)
2. [for arm64 architectures](https://seafile.unistra.fr/f/51bb8a3a2c9242f18f1a/?dl=1) , for a Raspeberry Pi for instance

Download the file ethercat-igh-install_1.0_amd64.deb or (ethercat-igh-install_1.0_arm64.deb) in the `/tmp` folder and install it with the following command:

### For amd64 architectures
```cd /tmp && sudo apt -f install ./ethercat-igh-install_1.0_amd64.deb && cd -```

### For arm64 architectures
```cd /tmp && sudo apt -f install ./ethercat-igh-install_1.0_arm64.deb && cd -```

### Use
Then you can use the install script to install the EtherCAT Master stack of IgH:

``` bash
sudo ethercat_igh_init
```

You just have to follow the instructions of the script.
Every parameter is in the file 
`/usr/share/ethercat_igh_dkms/ethercat_igh_dkms/parameters.py`

The default installation and parameters install the EtherCAT Master stack of IgH with the following parameters:
1. generic driver
2. version: stable-1.6
3. 1 master
4. the program guess the right ethernet interface
5. 1 ethernet interface selected in that order: ethX, enoX, ensX, enpXsY, enxFF:FF:FF:FF:FF:FF

If you want to let the program give you the choice for the ethernet interface, in the file `/usr/share/ethercat_igh_dkms/ethercat_igh_dkms/parameters.py` you have to set the parameter `guess_used_ethernet_interface` to `False`.

If some configuration is present, like when you have already installed the EtherCAT Master stack of IgH and you need to update your installation for a new linux kernel the script will reuse the installed configuration file and not ask any question.

If you want to bypass this behaviour and force the script to reconstruct the configuration file `/etc/sysconfig/ethercat` use:
``` bash
sudo ethercat_igh_init -o
```

### Other options

* `--skip_dependencies`: to skip dependency installation (build-essential, git, etc.)
* `skip_secure_boot_check`: to skip the secure boot check
* `-i, --interactive`: to force the script to be interactive or to be non-interactive (e.g. `sudo ethercat_igh_init --interactive false`)



### Help
To see the help message you can use the following command:
``` bash
sudo ethercat_igh_init --help
```

### Uninstall
If you need to change the installation, please uninstall the package and reinstall it. To uninstall the package use the following command:
``` bash
sudo dpkg --purge ethercat-igh-install
```
