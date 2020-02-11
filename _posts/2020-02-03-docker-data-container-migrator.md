---
layout: post
title: Tool to migrate Data only containers in your docker environment 
tags: [docker, tools,bash]
---

Docker Data container migrator 
==============================
This tool can be used to migrate data across the data containers.

Clone it here https://github.com/bhishekarora/ddcm.git

You can do a fork and send the pull requests, if it is aligned pull will be approved.

What is data container ?
=======================
Data containers hold data only and they don't run, mongo kind of database runs in a container and map volumes from data containers.
They are portable and you can export the complete data container in cloud/local environment by TARing it and SCPing it.

![container](https://bhishekarora.github.io/img/docker.png)


Wait a minute but what is this tool used for if they are portable ?
========================
Well this helps you migrate the directories and not the complete containers, if you want to move /data from dev container to /data 
on test container, we can use this tool.
![tool](https://bhishekarora.github.io/img/datamigratortool.png)

Remote migration can be done via the remote scrip in the above repo, check readme on how to enable docker daemon to listen 
remotely.

![remote](https://bhishekarora.github.io/img/remotedaemon.png)


To migrate complete containers just tar it

$docker export datacontainername >datacontainerbackup.tar and import it in the target env.


Upcoming features
===================

Will make it rsync between two data containers, autosync on a directory on both local and remote daemons.
