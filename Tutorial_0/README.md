# Tutorial 0: Setting up WSL and OpenFOAM

##  Table of Contents
- [Tutorial 0: Setting up WSL and OpenFOAM](#tutorial-0-setting-up-wsl-and-openfoam)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Setup](#setup)
    - [Step 1: Installing WSL](#step-1-installing-wsl)
    - [Step 2: Installing OpenFOAM](#step-2-installing-openfoam)
    - [Step 3: Installing ParaView](#step-3-installing-paraview)
    - [Step 4: Running a Test Case](#step-4-running-a-test-case)
    - [Clean Uninstall of WSL](#clean-uninstall-of-wsl)
  - [Conclusion and Troubleshooting](#conclusion-and-troubleshooting)
  - [References](#references)

## Introduction

In this tutorial, you will learn how to install the **Windows Subsystem for Linux** (`wsl`) and **OpenFOAM** version 11 on your **Windows** system. 

By following these steps, you will prepare your computer to use **OpenFOAM** for our upcoming simulations. Each step includes detailed instructions to make the installation process as smooth as possible, especially if you are new to working with **Linux** and terminal commands. 

We will be using the `.org` version of **OpenFOAM**, maintained by the [OpenFOAM Foundation](https://openfoam.org/). The `.org` version focuses on community-driven development and maintaining a consistent open-source philosophy. In contrast, the `.com` version, maintained by [OpenCFD Ltd](https://www.openfoam.com/), is more commercially oriented and includes proprietary features. Both versions share a common root, but for our educational purposes, the `.org` version is more suitable due to its open access and extensive community support.

> [!NOTE]
> This guide is intended for **Windows** users. If you are using **macOS**, please refer to the [OpenFOAM installation guide for macOS](https://openfoam.org/download/11-macos/).


## Setup

### Step 1: Installing WSL
Before you can run **OpenFOAM**, you’ll need to install `wsl` which allows **Windows** users to run a **Linux** environment directly on **Windows**, without the overhead of a traditional virtual machine.

1. Open `PowerShell` as "Administrator":
   - Right-click on the "Start" button and select "Windows PowerShell (Admin)".
2. List available **Linux** distributions:
   - To see what distributions are available for download, type:
     ```
     wsl --list --online
     ```
   - This command will display a list of all the **Linux** distributions that you can install. Popular choices for **OpenFOAM** include **Ubuntu**, **Debian**, or **openSUSE**.
3. Install the default **Linux** distribution:
   - Run:
     ```
     wsl.exe --install
     ```
   - Restart your computer to complete the installation.
5. Set up your **Linux** distribution:
   - After restarting, the **Linux** distribution terminal window should pop up automatically. If not, launch the new **Linux** terminal via the "Start" menu or by typing its name in `PowerShell` or `Command Prompt`.
   - Follow the prompts to set up your new user account and password.
6. Confirm the installation:
   - Verify that **Ubuntu 22.04 LTS** was installed by typing in the **Linux** terminal:
     ```
     lsb_release -a
     ```

### Step 2: Installing OpenFOAM
With your **Linux** set up, you are now ready to install **OpenFOAM**.

1. Update your **Linux** system's packages:
   - Update your **Linux** system's packages:
     ```
     sudo apt update
     sudo apt full-upgrade -y
     ```
2. Install dependencies required by **OpenFOAM**:
   - Run:
     ```
     sudo apt-get install build-essential
     ```
3. Download and install **OpenFOAM**:
   - Use the following commands:
     ```
     sudo sh -c "wget -O - https://dl.openfoam.org/gpg.key > /etc/apt/trusted.gpg.d/openfoam.asc"
     sudo add-apt-repository http://dl.openfoam.org/ubuntu
     sudo apt-get update
     sudo apt-get -y install openfoam11
     ```
4. Configure the **OpenFOAM** environment:
   - Add to your `.bashrc`:
     ```
     echo ". /opt/openfoam11/etc/bashrc" >> $HOME/.bashrc
     ```
   - Refresh the environment variables (note the dot):
     ```
     . $HOME/.bashrc
     ```
5. Confirm the installation:
   - Verify that **OpenFOAM** was installed correctly by running:
     ```
     foamRun -help
     ```
   - A "Usage" message should appear.
6. Your installation and user configuration are complete.

### Step 3: Installing ParaView
To visualize simulation results, you need to install **ParaView**. Since it's more stable on **Windows**, we recommend installing it directly.

1. Download the latest version of **ParaView** (`.msi`) from [**ParaView**'s official website](https://www.paraview.org/).
2. Install **ParaView** by following the on-screen instructions.
3. Once installed, you can open **ParaView** from the **Start** menu.

### Step 4: Running a Test Case
To ensure that your installation is functioning correctly, run a simple test case. The test case is taken from the tutorials directory which contains numerous example cases in **OpenFOAM**.

1. Explore the example cases:
   - The tutorials directory location is represented by the `$FOAM_TUTORIALS` variable in the **OpenFOAM** environment.
   - List the top-level contents of the `$FOAM_TUTORIALS` directory by typing in a terminal:
     ```
     ls $FOAM_TUTORIALS
     ```
2. Prepare your run directory:
   - The **OpenFOAM** environment includes a `$FOAM_RUN` variable which represents a directory in the user's file system at `$HOME/OpenFOAM/<USER>-11/run` where `<USER>` is the account login name and `11` is the **OpenFOAM** version number. This directory is the recommended location to store and run simulation cases.
   - Create the `run` directory by typing:
     ```
     mkdir -p $FOAM_RUN
     ```
   - Check if the directory exists by typing:
     ```
     ls $FOAM_RUN
     ```
3. Copy an example case:
   - Any example case from `$FOAM_TUTORIALS` can then be copied into the run directory. For instance, to try the lid-driven cavity example for the incompressible fluid solver module, copy it to the run directory by typing:
     ```
     cd $FOAM_RUN
     cp -r $FOAM_TUTORIALS/incompressibleFluid/cavity .
     ```
4. Run the example case:
   - Navigate to the cavity directory:
     ```
     cd cavity
     ```
   - Run the simulation by typing:
     ```
     blockMesh
     foamRun
     touch cavity.foam
     ```
5. Post-process the results using **ParaView**:
   - Copy the files from the `wsl` directory to a location in your **Windows** filesystem. This step might be necessary because **ParaView** on **Windows** might not have direct access to files within the `wsl` environment.
   - Launch **ParaView** on your **Windows** machine.
   - Use the "File -> Open" menu to navigate to the copied case files on your **Windows** filesystem and open the file with the extension `.foam`.
   - After opening the `.foam` file in **ParaView**, click the "Apply" button in the "Properties" panel on the left.
6. Here is what you should see if everything was done correctly:

   ![plot_ldc_raw](ldc_raw.png)

   - In the next tutorial you will learn how visualize and edit the solution as follows:

   ![plot_ldc_edit](ldc_edit.png)

### Clean Uninstall of WSL
This section provides a clear guide for users who want to completely remove `wsl` from their system and start over.

1. Uninstall your **Linux** distribution:
   - Open `PowerShell` as "Administrator".
   - List all installed `wsl` distributions:
     ```
     wsl --list --verbose
     ```
   - Uninstall the desired distribution (replace `<DistroName>` with the actual name, e.g., `Ubuntu`):
     ```
     wsl --unregister <DistroName>
     ```
2. Remove Ubuntu and Linux from Apps & Features:
   - Press `Win + I` to open "Settings", then navigate to "Apps > Apps & Features".
   - Search for "Ubuntu" and for "Linux" in the list, select it, and click "Uninstall".
   - If "Linux" does not appear in the list, open `PowerShell` as "Administrator" and use `winget` to find and uninstall it:
     ```
     winget list
     winget uninstall --name "Windows Subsystem for Linux" 
     ```
3. Uninstall WSL components:
   - Open `PowerShell` as "Administrator".
   - Disable `wsl` feature:
     ```
     dism.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart
     ```
   - Disable `Virtual Machine Platform` feature:
      ```
      dism.exe /online /disable-feature /featurename:VirtualMachinePlatform /norestart
      ```
   - Restart your computer to complete the uninstallation process.
4. For maintaining the health of your machine, it is recommended to run the following commands:
   - Clean up component store:
     ```
     dism.exe /online /cleanup-image /startcomponentcleanup
     ```
   - Repair system files:
     ```
     dism.exe /online /cleanup-image /restorehealth
     ```
   - Check `%LOCALAPPDATA%\Packages` and delete any leftover directories related to your `wsl` distribution.
   - Run disk cleanup by pressing `Win + R`, typing "cleanmgr", and pressing "Enter".
   - Run disk optimization by searching for "Defragment and Optimize Drives".
   - Verify System Integrity:
     ```
     sfc /scannow
     ```
   - These steps ensure your system remains clean and functional after uninstalling `wsl`.

## Conclusion and Troubleshooting
Congratulations! 

You should now have a functional **OpenFOAM** installation on your **Windows** machine, along with the ability to visualize results using **ParaView**. As you begin working with **OpenFOAM**, remember that learning to troubleshoot and solve problems is a valuable skill in computational engineering. Should you encounter issues, revisit the steps to ensure all commands were entered correctly. For further assistance, don’t hesitate to consult with the course TA or refer to the **OpenFOAM** community forums. By following this guide, you’re well on your way to performing complex fluid dynamics simulations. 

Happy computing!


## References
[https://openfoam.org/download/windows/](https://openfoam.org/download/windows/)

[https://openfoam.org/download/11-ubuntu/#getting-started](https://openfoam.org/download/11-ubuntu/#getting-started)

[https://doc.cfd.direct/openfoam/user-guide-v11/tutorials](https://doc.cfd.direct/openfoam/user-guide-v11/tutorials)
