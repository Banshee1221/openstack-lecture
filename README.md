# OpenStack Lecture 
## UWC - CS Honours 2017

### Assignment

#### Installing Devstack
1. Download your preferred virtualization software, such as Virtualbox or qemu, for your OS.
2. Find and download an Ubuntu 16.04 **SERVER** iso.
3. Install the Ubuntu 16.04 server image you downloaded in a virtual machine on your host OS.
   * **NB**: Configure the VM with **2 bridged** network adapters!!!
4. Once Ubuntu is installed, log in and run `sudo apt update && sudo apt dist-upgrade`
5. Reboot the virtual machine
6. Once logged in, run the following commands:
```bash
sudo useradd -s /bin/bash -d /opt/stack -m stack
echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
sudo su - stack
git clone https://git.openstack.org/openstack-dev/devstack
cd devstack
```
7. When in the devstack directory, create a file called local.conf and add the following to it:
```
[[local|localrc]]
ADMIN_PASSWORD=---the-password-you-want---
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
PUBLIC_INTERFACE=---name-of-the-second-network-card-not-used-for-ssh---
```
8. Run the `stack.sh` script
   * **NB**: The process will take quite some time to complete. Could be up to an hour.

#### Operating Devstack
Once devstack is up and running, you can navigate to the IP address of the virtual machine in your web-browser. Ex: `http://192.168.1.1/` Here you can log in with user: `admin` and password whateveryou defined above in the `local.conf` file.
##### Network
Log into the Dashboard, `Horizon` as admin and switch to the `demo` project. First step now is to create a network that will use the bridge you set up in `step 3` to allow you add virtual machines to the campus network.
1. Go to the Admin -> Network -> Networks tab
2. Select `Create Network`.
3. Name the network `campus`, give it the `demo` project and 

