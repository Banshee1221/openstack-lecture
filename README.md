# OpenStack Lecture 
## UWC - CS Honours 2017

### Assignment
1. Download your preferred virtualization software, such as Virtualbox or qemu, for your OS.
2. Find and download an Ubuntu 16.04 **SERVER** iso.
3. Install the Ubuntu 16.04 server image you downloaded in a virtual machine on your host OS.
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
ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
```
8. Run the `stack.sh` script
   * **NB**: The process will take quite some time to complete. Could be up to an hour.


