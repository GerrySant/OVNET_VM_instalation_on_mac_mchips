# OVNET Lab Setup Guide for Mac M1 and Later

This guide provides instructions on how to set up the `TCGI_OVNET_debian.ova` virtual machine for the Overlay Networks (OVNET) course at UPC using UTM Virtual Machines on a Mac with an M1 chip or later.

## Table of Contents
- [Preliminary Steps](#preliminary-steps)
- [Importing the OVA File](#importing-the-ova-file)
- [Setting Up UTM](#setting-up-utm)
- [Post-Installation](#post-installation)

## Preliminary Steps

### 1. Download UTM
- Download and install UTM Virtual Machines from the [Mac App Store](https://apps.apple.com/us/app/utm/id1505677402?mt=12).

### 2. Locate the OVA File
- Ensure you have the `TCGI_OVNET_debian.ova` file downloaded and accessible on your Mac.

## Importing the OVA File

### 1. Install Homebrew (If not installed)
- If you don't have Homebrew installed on your Mac, open Terminal and run the following command:
  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- Follow the on-screen instructions to complete the installation.

### 2. Extract the OVA File
- Open Terminal and navigate to the directory where the `.ova` file is stored.
  ```bash
  tar -xvf TCGI_OVNET_debian.ova
  ```
- This will produce an `.ovf` (XML-based config file) and a `.vmdk` (disk image).

### 3. Convert VMDK to QCOW2
- Install `qemu-img` via Homebrew:
  ```bash
  brew install qemu
  ```
- Convert the `.vmdk` to `.qcow2`:
  ```bash
  qemu-img convert -f vmdk TCGI_OVNET_debian-disk1.vmdk -O qcow2 TCGI_OVNET_debian.qcow2
  ```

## Setting Up UTM

### 1. Open UTM
- Launch the UTM app.

### 2. Create a New VM
- Click on the "+" button to create a new VM.
- **Click the "emulate"**.
- Click "other" in the custom section.
- Activate the "Skip ISO boot" option.
- Leave the rest of the configs as your needs or default.
- Continue & Save.

### 3. Configurating the new VM
- Open the configuration of the virtual machine just created.
- Within the pop-up Configuration window navigate to the Drivers section, located at the bottom left.
  - Delete existing drive (Mine is called IDE Drive)
  - Click in New...
  - Import
  - Select the qcow2
  - Go to QEMU Tab
  - Unselect "UEFI Boot"
  - Save
  - Run

## Post-Installation
- Use the login credentials provided by your professors. (Sometimes are not requested)
