---
title: "3-2-1 Backup Strategy"
date: 2025-08-19
draft: false
description: "A page about 3-2-1 backup strategies"
tags: ["example", "tag"]
---

# A tale of data
We live in a world of data, data runs your phone, your television, your car, and very likely your schedule as well. Well where does this data all live in the digital world? Great question, where does YOUR data live? I think that something we've lost track of in this overwhelming digital world is where does your important data live. Many of my most valuable photos live on my iPhone + iCloud (Apple Servers) what would happen if Apple's servers went down or they decided they just didn't like me anymore? Well hopefully all my precious photos would then live on my phone, but let's be honest some of us have photo libraries that have outgrown their phones minimal storage.

This isn't true for everyonee of course, but the point I'm trying to convey is that where your data lives needs to be understood for you to develop any sort of control over it.

That's my intro to 3-2-1, now let's talk about what 3-2-1 means.

## What is 3-2-1?
3-2-1 is a phrase that you'll probably hear if you have any co-workers or loved ones who work in technology or are tech hobbiests themselves. 

3-2-1 stands for lives in 3 copies of your data on at least 2 different storage locations with at least 1 of those devices offsite. 

What does this mean? Let's break it down.

If I have a file that lives on my desktop or laptop computer that's 1 copy of that data. I could also be a little smarter and backup that file on an external storage device like a SSD, HDD or NAS. That would be a 2nd copy of that data and that's great but accidents happen, maybe you lost that drive or in the worst case you lose your NAS in a basement flood, house fire, burgalary etc. that's why you have an offsite storage location, and this can be something like another NAS that you keep at your parents or friends house, or even an encrypted cloud provider. 

## My personal backup strategy
I am fortunate enough to have a few computers and I'm also a little obsessed with technology so I've got 1 Desktop Computer dual booted with Ubuntu and Windows, and a Macbook Laptop. This allows me to play around in every operating system (Mac is best, fight me). 

So my backup strategy is to have my Mac, Windows and Ubuntu computers all backup to my Synology NAS which lives in my basement, this device in turn backs up to Backblaze B2 as an encrypted backup. I've debated setting up a NAS at a friend or parents house, but honestly at this point it might just confuse them. So for now backblaze works flawlessly.

Additionally I have a 3 Node Proxmox Cluster that's comprised of 2 Lenovo Thinkcenter m715q's and 1 custom PC(an old PC I turned into a server). I use Proxmox Backup Server virtualized in the cluster to backup the cluster to my NAS as well.

## Don't forget restoration testing!!!

Here's the final piece I'll leave you with. **PLEASE, PLEASE, PLEASE** perform restoration tests with your data. It doesn't count as a backup if you can't restore from it. Things happen, data gets corrupted, backups sometimes don't complete fully. Make sure you have a schedule for testing your backups even if it's once a month. 

Not testing your backups is a recipe for disaster it's like writing a math equation without a proof, well that's nice but you haven't really proven that it works. 

Hopefully you enjoyed reading my short 3-2-1 Backup Strategy Article :)
