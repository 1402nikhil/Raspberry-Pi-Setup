# Raspberry Pi ROS2
This repository contains the setup procedure of ROS2 on the Raspberry Pi and the related codes for three omniwheel and differential drive robot.

## Raspberry Pi Imager Installation

- **Download**: [Raspberry Pi Imager – Official Download Page](https://www.raspberrypi.com/software/)

- **Installation Using APT**

 This method automatically resolves dependencies.

```bash
sudo apt install ./filename.deb
```

 Make sure to include `./` if the `.deb` file is in your current directory.

---

## OS Installation

- **OS**: Ubuntu MATE 22.04 (ARM64)  
- **Download**: [Ubuntu MATE 22.04 ARM64 (.img.xz 1.8 GB)](https://releases.ubuntu-mate.org/22.04/arm64/)

---

## Essential Software Installation

### Update System First
```bash
sudo apt update
```

### 1. Git
```bash
sudo apt install git
```

### 2. OpenSSH Server
```bash
sudo apt install openssh-server
```

### 3. ROS 2 Humble Installation

- Follow the steps mentioned in official documentation to instal ROS2 Humble.
- [ROS 2 Humble Official Installation Guide](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)

### 4. Xacro Installation
```bash
sudo apt install ros-humble-xacro
```

### 5. ros2_control and ros2_controllers Installation
```bash
sudo apt install ros-humble-ros2-control ros-humble-ros2-controllers ros-humble-hardware-interface
```
Custom Hardware Message Support
```bash
sudo apt install ros-humble-controller-manager ros-humble-control-msgs
```

### 6. Micro-ROS Setup
- Follow the instruction related to Micro-Ros agent setup mentioned in tutorial and the video.
- Micro-ROS Github: [Micro-Ros](https://github.com/micro-ROS)
- Micro-ROS tutorial:  [micro-ROS: First Application on RTOS (FreeRTOS)](https://micro.ros.org/docs/tutorials/core/first_application_rtos/freertos/)

- Reference Video: [Micro-ROS Robot using PlatformIO for ESP32 with ROS 2 – YouTube](https://youtu.be/Nf7HP9y6Ovo?si=GkxALOkdCVXuOAPu)

- Agent Run Command

```bash
ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyACM0
```

### 7. Wireless Controller Setup

```bash
sudo apt install joystick jstest-gtk evtest
```

- **Reference**: [Easy wireless control for your homemade robot!](https://youtu.be/F5XlNiCKbrY?si=w5_Fh4ZzALmVeLq5)

---

## Network Configuration (Netplan)

Create or modify a file in `/etc/netplan/` (e.g. `01-netcfg.yaml`) with the following content:
This file is indentation sensitive!!

```yaml
network:
  version: 2
  renderer: NetworkManager

  wifis:
    wlan0:
      dhcp4: no
      addresses: [192.168.201.127/24]  # Static IP for laptop or Raspberry Pi
      gateway4: 192.168.201.105        # IP of host/router/hotspot
      nameservers:
        addresses: [192.168.201.105]
      access-points:
        "Nikhil's M55":
          password: "Nikhil2000"
```

Apply configuration:
```bash
sudo netplan apply
```

---

## Remote Development

### VS Code SSH Setup

- Install the **Remote - SSH** extension by Microsoft in VS Code.

---

## Issues

### PlatformIO Python Interpreter Fix

- [Install PlatformIO-compatible Python](https://docs.platformio.org/en/latest/faq/install-python.html)
>>>>>>> 9d1e8d55c068ae8bb1eb57d28b150a2ab6c163e2
