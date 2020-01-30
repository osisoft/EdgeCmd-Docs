---
uid: EdgecmdUtility
---

# EdgeCmd utility

Use the EdgeCmd command line utility to configure and administer adapters on Linux and Windows. You can accomplish the same operations with EdgeCmd that you can accomplish with REST calls.

## Install EdgeCmd utility
Complete the following to install EdgeCmd utility on Windows or Linux.

### Windows

You must have administrative privileges to run the installer.

1. Copy the _EdgeCmd.msi_ file to the file system of the device.
2. To start the installer, double-click the _EdgeCmd.msi_ file in Windows Explorer.

   **Note:** You can choose an install path other than the default path of C:\Program Files\OSIsoft\EdgeCmd by entering the following command from the command prompt. OSIsoft recommends you use the default value.
    
    ```bash
    msiexec /i EdgeCmd.msi INSTALLFOLDER=<path_to_desired_location>
    ```

   **Note:** INSTALLFOLDER must be in all caps as shown in the preceding example.

The EdgeCmd utility is installed on your device.

### Linux

You must have administrative privileges to install the software, for example root or sudo privilege. The following examples assume a user with permission to use sudo.

1. Open a terminal window and type the sudo command for the appropriate EdgeCmd deb file for your processor:

    **Debian 9 or later (Intel/AMD 64 bit processors)**

    ```bash
    sudo apt install ./EdgeCmd_linux-x64.deb
    ```

    **Debian 9 or later (ARM32, Raspberry PI 2,3,4: Raspbian, BeagleBone)**

    ```bash
    sudo apt install ./EdgeCmd_linux-arm.deb
    ```

    ![alt text](https://osisoft.github.io/Edge-Data-Store-Docs/V1/images/LinuxInstall1.jpg "Linux Installation")

    **Debian 9 or later (Raspberry PI 3,4: Ubuntu ARM64 Server, Google Coral Dev Board, Nvidia Nano Jetson)**

    ```bash
    sudo apt install ./EdgeCmd_linux-arm64.deb
    ```

    A validation check for prerequisites will be completed. If the Linux OS is up to date, the install will succeed.

2. If the install fails, run the following commands from the terminal window and try the install again:

    ```bash
    sudo apt update
    sudo apt upgrade
    ```

    After the check for prerequisites succeeds, you will be prompted if you want to change the default port (5590).

The install will complete and the EdgeCmd utility will be running on your device.
