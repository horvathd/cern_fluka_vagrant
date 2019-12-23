# Installing CERN's FLUKA and Flair on Windows using Vagrant

It is recommended to use the Windows Subsystem for Linux (WSL) for running CERN's FLUKA and Flair on Windows 10.
However if you are using an Windows 7, 8 or an older build of Windows 10, WSL is not available to you.
In that case you can use a virtual machine to run FLUKA.
Vagrant allow the easy configuration and management of a VirtualBox virtual machine.

## 1. Required software

### 1.1. Vagrant

Download Vagrant from [vagrantup.com](https://www.vagrantup.com/) and install it. After the installation restart Windows.

### 1.2. VirtualBox

Download VirtualBox from [virtualbox.org](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) and install it. Vagrant currently doesn't support version 6.1.

### 1.2. Install Xming

Xming X Server for Windows is necessary to visualize the Flair's graphical interface.

Download and install the *Public Domain Release* version from http://www.straightrunning.com/XmingNotes/

## 2. Setting up and using the virtual machine

### 2.1. Configuration file

Download the configuration files from [here](https://github.com/horvathd/cern_fluka_vagrant/archive/master.zip), and extract it.
It contains the *Vagrantfile* storing the configuration of the virtual machine and a *FLUKA* folder.

### 2.2. Start a Command Prompt

Start a Command Prompt as Administrator, and change to the folder where the *Vagrantfile* is located.

### 2.3. Start the virtual machine

Simply use the

> `vagrant up`

command. The first time you run, vagrant will download and configure the base for the virtual machine, which could take some time.
Later the start should take around 20 seconds only.

### 2.4. Start Xming

Start the *XMing* app from the *Start Menu*.

### 2.5. Connect to the virtual machine

To connect use the command:

> `vagrant ssh`

When you see the

> `vagrant@fluka:~$`

prompt, the virtual machine is ready to use.

### 2.6. Shared folder

In the Windows machine The *FLUKA* folder next to the *Vagrantfile* is automatically shared with the virtual machine at `/fluka` directory.

### 2.7. Log out fron the virtual machine

Use the

> `logout`

command.

### 2.8. Stopping the virtual machine

the command

> `vagrant halt`

will shut down the virtual machine

### 2.9. Deleting the virtual machine

In case you don't need the virtual machine any more, or you want to restart from a clean state, you can delete the virtual machine with

> `vagrant destroy`

The shared folder on Windows won't be deleted.

## 3. Installing FLUKA and Flair

### 3.1. Setting up Ubuntu for FLUKA and installing Flair

Run the *setup_vagrant_ubuntu-18.04.sh* script available at `/fluka` in the virtual machine:

> `sudo ./setup_wsl_ubuntu-18.04.sh`

The script will install the necessary packages, configure *gfortran 8*, and install Flair. After the installation
finished, restart *Ubuntu*.

### 3.2. Installing FLUKA

You can follow the installation steps for GNU/Linux to install the *gfor9.tgz* package of FLUKA, on
[fluka.cern](https://fluka.cern/documentation/installation/fluka-linux-macos)

### 3.3. Running FLUKA and Flair

See the instructions on [fluka.cern](https://fluka.cern/documentation/running)

## 4. Updating FLUKA and Flair

### 4.1. Update Flair

To update Flair (and *Ubuntu* as well) run the following commands:

> `sudo apt-get update`

> `sudo apt-get upgrade`

### 4.2. Update FLUKA

Manually install the latest package of FLUKA.
