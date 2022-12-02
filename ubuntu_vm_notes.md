### installing a virtual machine to test ssh connection

# virtual machines
[tutorial on creating virtual mnachines with the terminal](https://phoenixnap.com/kb/ubuntu-install-kvm#ftoc-heading-8)
<br> <br>
## 1. Check Virtualization Support on Ubuntu 20.04
<pre>
<code>
$ egrep -c '(vmx|svm)' /proc/cpuinfo
</code>
</pre>
output: 8
<br>

If the command returns a value of 0, your processor is not capable of running KVM. On the other hand, any other number means you can proceed with the installation.
<br>

Now, check if your system can use KVM acceleration by typing:
<pre>
<code>
$ sudo kvm-ok
</code>
</pre>
If kvm-ok returns an error stating KVM acceleration cannot be used, try solving the problem by installing cpu-checker.

<pre>
<code>
$ sudo apt install cpu-checker
</code>
</pre>
When the installation completes, restart the terminal.
<br> <br>
## 2. Install KVM on Ubuntu 20.04
<pre>
<code>
$ sudo apt update
</code>
</pre>

<pre>
<code>
$ sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
</code>
</pre>

Only members of the libvirt and kvm user groups can run virtual machines. Add a user to the libvirt group by typing:

<pre>
<code>
$ sudo adduser ‘joris’ libvirt
</code>
</pre>
do the same for kvm
<pre>
<code>
$ sudo adduser ‘joris’ kvm
</code>
</pre>

Confirm the installation was successful by using the virsh command:
<pre>
<code>
$ virsh list --all
</code>
</pre>
<br> <br>
## 3. Creating a Virtual Machine on Ubuntu 20.04
<pre>
<code>
$ sudo apt install virt-manager
</code>
</pre>

<pre>
<code>
$ sudo virt-install --name=ubuntuvm --description='ubuntuvm' --ram='1536' --vcpus=1 --disk path=/var/lib/libvirt/ubuntuvm/ubuntuvm.qcow2,size=15 --cdrom /home/joris/ubuntu-img.iso --graphics vnc
</code>
</pre>

<br> <br>
## 4. use the virtual machine to make an ssh connection tot the host machine
open the virtual manager and run the virtual machine 
<pre>
<code>
$ virt-manager
</code>
</pre>

if the login page does not appear, use ctrl+d to open it.

[ssh tutorial to ssh into remote host with ubuntu](https://www.youtube.com/watch?v=Wlmne44M6fQ)
go to the remote server you want to acces, and execute the following commands

<pre>
<code>
$ sudo apt update
</code>
</pre>
if openssh is not installed yet, install it
<pre>
<code>
$ sudo apt install openssh-server
</code>
</pre>
check if openssh is enabled
<pre>
<code>
$ sudo systemctl status ssh
</code>
</pre>
output: it needs to be set to active (running)
<br>
we need to make sure that the port ssh (port 22 ) is open, and the firewall will allow ssh
<pre>
<code>
$ sudo ufw allow ssh
</code>
</pre>
we need to use the remote servers'ip adress. We can acces it through
<pre>
<code>
$ ip a
</code>
</pre>
now, we move to the control server and ssh into the remote server
<pre>
<code>
$ ssh joris@192.168.74.133
</code>
</pre>
and press enter

![image](./images/a.jpg)

quit the connection
<pre>
<code>
ctrl+d
</code>
</pre>


as a test, we can also reverse the connection

![image_revers](./images/b.jpg)

































