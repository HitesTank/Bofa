# Setup CRC Containers on Local 

Openshift comes with flavors and each has its specific usage. In order to learn, you can install Openshift locally with RedHat CodeReady Containers.

Earlier, minishift were used to install Openshift OKD which is open source version with Openshift 3.11.

For installing Openshift 4 locally, RedHat CodeRady Containers are made available, which you can use to to run.


# Install CodeReady Containers.

CodeRady Contaiiners, has single node configuraton and it operates exactly like Minishift.

CRC(CodeReay Containers) runs on native hypervisor, KVM for Linux, HyperKit for macOS, and Hyper-V for Windows. Following steps have been considered for Ubuntu.

## Installations.
VirtualBox is not supported so, KVM must be installed first.

### KVM Installation
Please perform following steps to install KVM, you can skip this step if you already have it.

```
$ sudo apt-get install qemu-kvm libvirt-bin virtinst bridge-utils cpu-checker
```
```
$ kvm-ok
```

### CRC Installation

RedHat has provided CRC installaton guide, to access this guide you need login into RedHat Account or Register for free.

The installation guide contains download link for CodeReady Containers for Linux, macOS, and Windows.

[CRC Installation Guide](https://cloud.redhat.com/openshift/install/crc/installer-provisioned)

The installation guide contains hardware requirements which can found below:


Markup: * 4 virtual CPUs (vCPUs)
        * 9 GB of RAM
        * 35 GB of disk space for the virtual disk

Downloaf CodeReady Containers from archive and download the pull secret to local location.

Extract crc file and place it into /usr/local/bin/

Folow below commands to setup CodeReady Containers

```
$ crc setup
```

This will run the check for prerequisites, and create .crc directory.

Add the pull secret file paht which was downloaded from RedHat site. This pull secret will be used to download container images from the RedHat registry.

```
$ crc config set pull-secret-file path/to/pull-secret.txt
```

Initialize and start CodeReady Containers with following command

```
$ crc start
```
This takes a while, and once finish it will show instructions to access Openshift console.

Even after the start command finish it takes few more minutes to start, but you can still check its status

```
$ crc status
```

Now, once you get the status running you can actually acces openshift cluster using below command.

```
$ crc console
```
You can login with user kubeadin if you want to be cluster admin.

Below are some more commands you may need

```
$ crc stop
$ crc delete
```
