
# Automated Setup Scripts for Hetzner VPS and Proxmox VE

## Overview
This repository contains two scripts:
1. **hetzner-debian12-zfs-setup.sh**: Installs Debian 12 with ZFS as the root file system on a Hetzner VPS.
2. **proxmox_install.sh**: Installs Proxmox Virtual Environment (VE) on Debian 12.

## Usage

### 1. Hetzner Debian 12 with ZFS Setup
**Script:** `hetzner-debian12-zfs-setup.sh`  
**Description:** This script automates the setup of Debian 12 with ZFS root on Hetzner VPS. It prepares ZFS pools, partitions disks, and installs Debian 12 on the root ZFS filesystem.

#### Steps to Use:
1. In the Hetzner rescue system:
   - Set the OS to `linux64`.
   - Add your SSH key.
   - Click "mount rescue and power cycle."
2. SSH into the console after reboot and run the script:
   ```bash
   ./hetzner-debian12-zfs-setup.sh
   ```
3. Follow prompts to configure:
   - Hostname
   - ZFS ARC cache size
   - Disk selections for ZFS pools
   - Swap size and free tail space
   - Root password
   - Encryption options for the root pool

**Note:** Run the script in a `screen` session to prevent disconnections:
   ```bash
   screen -dmS zfs
   screen -r zfs
   ```

### 2. Proxmox VE Install on Debian 12
**Script:** `proxmox_install.sh`  
**Description:** This script installs Proxmox VE on Debian 12, adding Proxmox repositories, installing necessary packages, and configuring the environment.

#### Steps to Use:
1. SSH into your Debian 12 server.
2. Run the script:
   ```bash
   ./proxmox_install.sh
   ```
3. The script will:
   - Add Proxmox repository and update the system.
   - Install the Proxmox kernel and required packages (Proxmox VE, Postfix, Open-iSCSI, and Chrony).
   - Reboot automatically after major installation steps.

## Warnings
- **Data Loss:** Running `hetzner-debian12-zfs-setup.sh` will erase all data on the selected disk.
- **Internet Connection:** Both scripts require an active internet connection to download packages.
