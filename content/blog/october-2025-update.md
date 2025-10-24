---
title: "October 2025 Status Update"
date: 2025-10-20T22:00:59+01:00
draft: false
---

This is my first blog post documenting the development of the **MONOLITH project**.

[MONOLITH](https://github.com/MONOLITH-Project) is an operating system I have been working on since the month of march this year, my progress on it has been quite slow, and it has stalled in the last month for different reasons including my struggle with motivation, my comeback to college and my new job.

But I'm coming back with new ideas and plans for the project!

![Brutal Screenshot](the-monolith.webp)

## The current state of the project

Currently, the operating system is in a pretty half-baked state with basic functionality that includes physical and virtual memory management, a heap allocator, a VFS, tmpfs, and more...

I have also an ELF-loader capable of loading executables in usermode, support for a few syscalls and I made a little bit of progress on task switching.

The functionality for loading executables into usermode is very far from complete, as there's still no support for multitasking, and also no memory protection for usermode "processes" (which makes the whole usermode thing useless).

I have also ported a demo of [microui](https://github.com/rxi/microui/) to this operating system, which was suprisingly very straightforward to port and it runs pretty smoothly as well!

{{< rawhtml >}}
<video controls width=auto>
  <source src="monolith-microui-demo.mp4" type="video/mp4">
</video>
{{< /rawhtml >}}

## Now what?

### The operating system

My biggest plan for the operating system that I have been working on is to abandon it, and fork an existing operating system which is [Brutal](https://brutal.smnx.sh/).

**Brutal** is a microkernel, capability based and Unix-like operating system made by [Clem](https://smnx.sh/) and [Cyp](https://cyp.sh/), and it's one of many projects that inspired me to get into the hobby osdev field, but this project has been abandoned in a very incomplete state for over 2 years, since its developers have gotten busy working on other projects like [SkiftOS](https://skiftos.org/) and [WingOS](https://github.com/supercip971/wingos).

![Brutal Screenshot](brutal.webp)

**Brutal** in its current state has most the basic foundation for a functioning microkernel which includes the IPC, syscalls, scheduling and SMP, in addition to some UI and graphics support. but it still lacks a filesystem (or even a VFS), terminal support, and the UI is barely functional at all.

With all of that in mind, I believe Brutal is a good candidate for a starting point for an operating system project.

### Why fork an existing operating system?

This is a very good question!

The best reason is that there are just way too many operating systems made by hobbiests, and most of them are left abandoned and in a very half-baked state, and this is one of the major problems in the ecosystem of hobby osdev, the community is too distracted and fragmented.

As a result of this fragmentation, we have plenty of indie operating system projects, but hardly none of them are in a stable or a usable state, and by forking an existing operating system this would contribute to making the indie osdev ecosystem just a little bit more mature.

### The programming language

I had previous plans to work on a programming language called **Dash** that targets the [UXN virtual machine](https://100r.co/site/uxn.html), but I'm dropping this idea.

My new plan is to make a portable, statically typed and interpreted programming language that would be used to develop applications for **MONOLITH**.

For now I'm working on writing a draft for the specification of the language before implementing it.

### The virtual machine

![HAL 9000](hal9000.webp)

I'm considering implementing **Dash** as a managed language targeting my own virtual machine, I have prototyped before a virtual machine called [HAL64](https://github.com/mrunix00/HAL64), this virtual machine is a stack based machine with support for register based instructions, and in my testing it was able to achieve very good performance for a non-JIT virtual machine.

I might pick up that project and integrate it into **MONOLITH** ecosystem, although I really love the name **HAL64** I might consider changing it to something else since **HAL** in operating systems usually stands for **Hardware Abstraction Layer**.
