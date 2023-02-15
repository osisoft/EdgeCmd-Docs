---
uid: InstallEdgeCmdUtility
---

# Install EdgeCmd utility

You can install EdgeCmd utility on either a Windows or Linux operating system. For more information, see [System requirements](xref:SystemRequirements).

**Note:** EdgeCmd utility does not have a user interface or installation prompt.

## Windows

**Prerequisite:** Contact your IT department to ensure that you have administrative privileges necessary on the local machine to run the install kit.

Complete the following steps to install EdgeCmd utility on Windows:

1. Download the `EdgeCmd_1.3.0.27-x64_.msi` file from the [OSIsoft Customer portal (https://customers.osisoft.com/s/products)](https://customers.osisoft.com/s/products).

    **Note**: Customer login credentials are required to access the portal.

2. Run the .msi file.

   **Note:** To change the install path from the default path of *C:\Program Files\OSIsoft\EdgeCmd*, enter the following command in the command prompt and update the *<file_path>*. OSIsoft recommends you use the default value.

    ```bash
    msiexec /i EdgeCmd.msi INSTALLFOLDER=<file_path>
    ```

   **Note:** You must type INSTALLFOLDER in all caps.

EdgeCmd utility is installed on your device.

## Linux

**Note:** You must have administrative privileges to install the software, for example, root or sudo privilege.

Complete the following steps to install EdgeCmd utility on Linux:

1. Open a terminal window and type the sudo command for the appropriate EdgeCmd .deb file for your processor:

    **Debian 9 or later (Intel/AMD 64-bit processors)**

    ```bash
    sudo apt install ./EdgeCmd_1.3.0.27-x64_.deb
    ```

    **Debian 9 or later (ARM32, Raspberry PI 2,3,4: Raspbian, BeagleBone)**

    ```bash
    sudo apt install ./EdgeCmd_1.3.0.27-arm_.deb
    ```

    **Debian 9 or later (Raspberry PI 3,4: Ubuntu ARM64 Server, Google Coral Dev Board, Nvidia Nano Jetson)**

    ```bash
    sudo apt install ./EdgeCmd_1.3.0.27-arm64_.deb
    ```

    A validation check for prerequisites is completed.

    **Note:** The default installation location is `/opt/OSIsoft/EdgeCmd`.

2. After the check for prerequisites succeeds, accept the default port number `5590` or change the port number.

    If the Linux OS is up-to-date, the install succeeds and EdgeCmd utility starts running on your device.

3. If the install fails, run the following commands from the terminal window and try the install again:

    ```bash
    sudo apt update
    sudo apt upgrade
    ```
