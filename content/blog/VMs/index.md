---
title: "Virtual Machines"
date: 2025-03-05
description: "Why have just 1 Operating System?"
layout: "index"
draft: false
showAuthor: false

---

## Virtual Machines in my Homelab

I started out with a Raspberry Pi in my homelab, it's the gateway drug. It's a cliche and I know it, but thanks to that amazing little computer, I was immediately interested in learning more about how you can host servers in your own home network. Having almost 0 practical work expereience in working with servers, I figured I'd get a little knowledge under my belt, so I decided to start a learning journey. 

I had seen plenty of material online about the CompTIA Certifications so I started at the basics, I started taking CompTIA A+ courses with Mike Myers and it was amazing, 
I had so much fun learning about all the basics of IT. 

What really struck me though was the section on virtual machines. I was shook, you could ostensibly emulate any operating system you wanted to on any hardware that you owned (and even some hardware that you rent through something like a virtual private server or [VPS](placeholderlinkforlater))

This is where I really got a dive into Linux for the first time, but you're here to learn about virtual machines so lets start on that

## What is a Virtual Machine
A virtual machine in short is virtualized hardware on your machine that usually hosts an operating system of your choosing, this is managed by something called a hypervisor. 

A hypervisor is simply put software that manages virtual machines and their allocation. 

There are 2 types of Hypervisors (there may be more but as of right now I'm only familiar with the two). A type 1 hypervisor or "bare metal" hypervisor, is a hypervisor that acts as your operating system. In my homelab this is [Proxmox](https://www.proxmox.com/en/). This manages each and every one of my virtual machines.

