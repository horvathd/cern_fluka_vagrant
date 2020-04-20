# Installing CERN's FLUKA and Flair on Windows using Vagrant

It is recommended to use the Windows Subsystem for Linux (WSL) for running CERN's FLUKA and Flair on Windows 10.
However if you are using an Windows 7, 8 or an older build of Windows 10, WSL is not available to you.
In that case you can use a virtual machine to run FLUKA.
Vagrant allows easy configuration and management of a VirtualBox virtual machine.

## 1. Required software

### 1.1. Vagrant

Download Vagrant from [vagrantup.com](https://www.vagrantup.com/) and install it. After the installation restart Windows.

### 1.1.1. Install Guest Addtion Plugin for Vagrant

Run the following command in a command prompt to install the Guest Addtion Plugin for Vagrant:

> `vagrant plugin install vagrant-vbguest`

### 1.2. VirtualBox

Download VirtualBox from [virtualbox.org](https://www.virtualbox.org) and install it.

### 1.3. Xming

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

If there is an error with the shared folder due to the missing *VirtualBox Guest Additions*, run the following command:

> `vagrant provision && vagrant vbguest && vagrant reload`

### 2.4. Start Xming

Start the *Xming* app from the *Start Menu*.

### 2.5. Connect to the virtual machine

To connect use the command:

> `vagrant ssh`

When you see the

> `vagrant@fluka:~$`

prompt, the virtual machine is ready to use.

### 2.6. Shared folder

In the Windows machine the *FLUKA* folder next to the *Vagrantfile* is automatically shared with the virtual machine at `/fluka` directory.

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

## 3. Installing, running, and updating FLUKA and Flair

Use the instructions starting from **Point 2** at https://fluka.cern/documentation/installation/fluka-flair-windows10-wsl 
