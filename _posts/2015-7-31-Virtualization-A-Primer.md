---
layout: post
title: Virtualization: A primer
---
## What is virtualization? ##
Virtualization, to keep things simple and short, is simply the act of creating a virtual (not actual) computer resource (usually within another computer resource.)  In this short post, I will discuss some ways to virtualize an operating system and compare them.  
### Virtual Machines ###
Virtual machines are full fledged virtualized computers.  The virtual machines themselves, or VM for short, are managed by a piece of technology called a hypervisor.  There are two types of hypervisors: type 1 and type 2.
#### Type 1 Hypervisor ####
A type 1 hypervisor is one that runs on 'bare metal', meaning that the Hypervisor itself acts as the host machine's operating system (of sorts) and that the hypervisor doesn't require a host operating system underneath.  These are the best option when considering the performance of the virtual machine and require the least overhead from the physical machine running the hypervisor software.  Examples include Xen, ESX/ESXi and HyperV.
#### Type 2 Hypervisor ####
Type 2 hypervisors run on an existing operating system and provision the virtual machines in a purely software manner.  They are convenient, because they can be installed on top of an existing operating system and don't require a dedicated computer, but they are less performant and use more overhead compared to type 1 hypervisors.  Examples include VirtualBox and VMWare Workstation.
### Containers ###
Containers are a relatively new technology that can achieve operating system or service virtualization and require less overhead from the host machine when compared to using virtual machines.  This is because every container shares the use of the host's kernel, while still allowing for user-space independance and also allows for services to be hosted without the need for an entirely independant operating system for each software container.  Like virtual machines, container hosting is available as a software that exists on a normal operating system (docker on top of linux, for example) or as a bare metal service.  Infrastructure as a Service, the mentality behind the drive to use bare metal container hosting, is becoming a more popular choice for hosting services, and provides the slimmest overhead available relative to software based containers and any kind of traditional virtualization technology.  Examples of these bare metal container services include JoentCloud's Triton service and Rackspace's OnMetal service.  These services are worth checking out because they stretch the hosting dollar the furthest, allowing the savvy to host more with fewer physical machines.
