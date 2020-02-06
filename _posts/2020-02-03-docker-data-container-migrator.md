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

Upcoming features
===================
Will be adding features to send the data to remote docker daemons on cloud via ssh , e.g move /data from dev@local to /data on 
test@remote/cloud

Will make it rsync between two data containers, autosync on a directory on both local and remote daemons.
