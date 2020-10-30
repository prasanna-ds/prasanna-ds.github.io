---
layout: post
title: "What do you need to know about containers and images?"
date: 2020-04-18 17:02:00 +0000
categories: [containers]
---

## Containers:

By this time, we all must be knowing about/working on docker. But, we need to know what is a container and an image before we jump right into dockerizing.

### What is a container?

          Containers are isolated process(es)
          
First of all, Containerization is not new!

Yes, containers have been around for a long time. There is always some level of isolation in all the operating systems. Let's see how containers have evolved over time,

*1979 - chroot* (change root) - Changes the root directory for the running process and its child processes.

*2000 - Jails* - Built upon the chroot, as with chroot, the isolations are limited to only the filesystem and the system resources, networks are shared by the chrooted processes and the other processes of the host system. Also, Chrooted processes are not secure that one can get out of the isolation. So, jails provide more isolation in terms of system resources and networking subsystems.

*2007 - LXC* - Linux containers - They provide system-level virtualization for running isolated containers in a single Linux kernel.

*2009 - Mesos* - Uses Linux cgroups for CPU, memory and I/O isolation.

*2013 - LMCTFY* - by Google, an acronym for Let Me Contain That For You, OS level virtualization based on Linux Cgroups which was later outsourced to Docker Inc.

*2013 - Docker by Docker Inc* - Container system, which initially used LXC containers and moved on with their own https://www.docker.com/blog/docker-0-9-introducing-execution-drivers-and-libcontainer/ and now they call it as runc https://github.com/opencontainers/runc which is based on OCI specifications.

*2015 - Kubernetes* - Container management/orchestration system for application deployments.

So, now we know what is a container and how containers have evolved, we need to know what makes up a container,

### Cgroups

Limits and isolates the resource usage, CPU, memory, I/O, the network of a process or a collection of processes.

### Namespaces

Isolates the global system resources that it makes it appear for a process that they have their own isolated instance of the global system in the namespace. There are types of namespaces,

*pid* - Process Ids (process ids are usually nested).

*mnt* - Isolates the mount point for the filesystem.

*ipc* - Isolates the interprocess communication resources.

*user* - Responsible for per-namespace mapping of userIds and groupIds.

*uts* - Responsible for domain and hostname isolations.

*network* - Virtualizes the network stack (for e.g. ports)

So, in short,

Cgroups limit how much we can use from global resources.

Namespaces limit what we can see of the global system.

To illustrate both of them in a diagram(i feel that cgroup is also part of the namespace),

![Containers](https://raw.githubusercontent.com/prasanna-ds/agusmakmun.github.io/master/static/img/_posts/Containers.png)

Now that, we know what is a container and what makes up a container, let's look at what an image is,

## Images:

Images are used to create a file system. It is a single file with FS snapshot and all the dependencies and probably a startup command for running the container.

So, finally to put them together,

A container is a running instance of an image with a set of resources assigned.

So, I think I have put in the basic concepts of containers and images in a nutshell before we containerizing our applications.

I hope this post was informative and let me know your comments in the box if you find it useful or something wrong in the content :)

See you soon!!!

Prasanna.

References:

http://man7.org/linux/man-pages/man7/namespaces.7.html

https://www.docker.com/blog/docker-0-9-introducing-execution-drivers-and-libcontainer/

https://github.com/opencontainers/runc
