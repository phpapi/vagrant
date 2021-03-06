# Docker vs. Vagrant

## History

Vagrant was first started as a personal side-project by Mitchell Hashimoto in January 2010. The first version of Vagrant was released in March 2010. In October 2010, Engine Yard declared that they were going to sponsor the Vagrant project. The first stable version, Vagrant 1.0, was released in March 2012, exactly two years after the original version was released. In November 2012, Mitchell formed an organization called “HashiCorp” to support the full-time development of Vagrant; Vagrant remained liberally licensed open-source software. HashiCorp now works on creating commercial additions and provides professional support and training for Vagrant.

Vagrant was originally tied to VirtualBox, but version 1.1 added support for other virtualization software such as VMware and KVM, and for server environments like Amazon EC2.[5] Vagrant is written in Ruby, but it can be used in projects written in other programming languages such as PHP, Python, Java, C#, and JavaScript.[6][7] Since version 1.6, Vagrant natively supports Docker containers, which in some cases can serve as a substitute for a fully virtualized operating system.[8]

## before

Vagrant was originally tied to VirtualBox, but version 1.1 added support for other virtualization software such as VMware and KVM, and for server environments like Amazon EC2.[5] Vagrant is written in Ruby, but it can be used in projects written in other programming languages such as PHP, Python, Java, C#, and JavaScript.[6][7] Since version 1.6, Vagrant natively supports Docker containers, which in some cases can serve as a substitute for a fully virtualized operating system.

## About VM
With the huge growth in virtualization and cloud computing, there has also been a correspondent increase in the average number of virtual machines (VM) that today’s admin has to manage. Manually creating a full VM on today’s virtualizers, like VMWare and Hyper-V, is a real pain because they have to take a snapshot of the entire machine config, and then replicate this to another machine. As you can imagine, VM images eat up a lot of space and time.

But some bright spark observed how VM’s operate and decided the model needed improvement. You see, a virtualizer works by creating a package or image containing an entire OS and machine setup, including hard drive, virtual processors and network interfaces. This is inefficient – oftentimes what you really want to recreate is just the OS platform and some apps. Is there a better way of doing this? As it turns out yes, although with some caveats. And Docker and Vagrant are two such solutions that take different roads to solving the limitations of the traditional VM.

## What They Are
Docker, previously called dotCloud and open-sourced in 2013, is a Linux-only virtual environment (VE) tool, not a VM tool. It builds on LxC (LinuX Containers), which uses the cgroups functionality to enable creation and running of multiple isolated Linux virtual environments (VE) on a single control host. So unlike a VM, a VE like Docker doesn’t create its own virtual computer with a distinct OS and processors and hardware emulation. A VE is VM-lite; it rides on the already existing kernel’s image of the underlying hardware, and only creates a ‘container’ in which to run your apps, and even recreate the OS if you want since the OS is also just another app running on the kernel. It places only a little extra load on the system, so unlike the traditional VM there is very little overhead when using Docker. Because of the shared kernel, Docker’s isolation is not as good as a full VM’s, but it suits many people just fine.

Vagrant, an open-source product released in 2010, is best described as a VM manager. It allows you to script and package the VM config and the provisioning setup. It is designed to run on top of almost any VM tool – VirtualBox, VMWare, AWS, etc. However, default support is only included for VirtualBox, for the other providers you must first install their plugins (http://docs.vagrantup.com/v2/providers/ ). However, Vagrant is still a virtual machine, albeit one with more powerful features than the bog-standard VM tools out there; for instance you can integrate Vagrant with CM tools such as Puppet and Chef to provision your own VM setups and configs.

## How They Work
Docker is really an extension of LxC, which is itself a sort of supercharged Linux chroot. LxC can only isolate not just your installed applications, but even the entire OS. What Docker does is give you the ability to snapshot the OS and apps you want into a common image, then easily deploy this image on other Docker hosts; this reveals another caveat – the machine you’re deploying to must also have Docker preinstalled. Docker is written in the lightweight Go language, and it uses helper scripts to create containers as lightweight machines. Docker builds on LxC’s and cgroups’ abilities by adding the following features:

Portable deployment across machines: you can use Docker to create a single object containing all your bundled applications. This object can then be transferred and quickly installed onto any other Docker-enabled Linux host.
Versioning: Docker includes git-like capabilities for tracking successive versions of a container, inspecting the diff between versions, committing new versions, rolling back etc.
Component reuse: Docker allows building or stacking of already created packages. For instance, if you need to create several machines that all require Apache and MySQL database, you can create a ‘base image’ containing these two items, then build and create new machines using these already installed.
Shared libraries: There is already a public registry (http://index.docker.io/ ) where thousands have already uploaded the useful containers they have created. Again, think of the AWS common pool of different configs and distros – this is very similar.
For an exhaustive list of Docker’s capabilities, see this Stackoverflow answer: http://stackoverflow.com/questions/17989306/what-does-docker-add-to-just-plain-lxc

Vagrant, on the other hand, still creates VM’s, although these are still lighter than the full-fat VM’s created by VM emulators. Vagrant provides a reproducible way to generate fully virtualized machines using Oracle's VirtualBox, AWS or VMWare technology as providers. There is a plugin called vagrant-libvirt, which adds support for libvirt to Vagrant.

## Conclusion

Interestingly, although Vagrant and Docker appear to be competitors, some enterprising admins have found a way to use them to actually complement each other. In such a scenario, Vagrant is used to create a base VM, then when you need to create different configs that all utilize this base VM, use Docker to provision and create different lightweight versions. See this discussion thread for an excellent explanation of how Docker does its magic: http://stackoverflow.com/questions/16047306/how-is-docker-io-different-from-a-normal-virtual-machine?rq=1.

If your main need is isolation and you require to quickly create several different VE images, then definitely use Docker. Docker is also ideal for environments in which you’re testing several short-lived images, such as when you need different scenarios for testing or debugging software. Vagrant is better when you require full VM’s and full isolation for those VM’s.