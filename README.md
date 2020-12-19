# vmall

## Purpose

Create and manage many libvirt vms easily

## Description

libvirt and virsh is awesome but they are not enough (for me) when you need hundereds of vms. So I created this script. Which helps provisioning and managing many vms on a single host just by ssh. I have used those vms mainly for docker swarm so there is an "swarm-init" option in the script but you don't have to use it.

## How To

You should create a file named "vmall.settings" in your current directory where you run this command. You may use "vmall.settings.sample" as a reference for your own "vmall.settings" file. 

This file should be adjusted according to your network/ip configuration. You also need to configure your DHCP or /etc/hosts file to make your vm ip be resolvable from vmnames. This script has an option "hosts" which creates a list of hostnames and ips for your vms which is suitable to be imported into your /etc/hosts file. Let's assume you use sample settings file then your vms will be named lie "vm101, vm102, vm103 ... vm200" and their local ips will be like "192.168.100.101, 192.168.100.102, 192.168.100.103, ... 192.168.100.200" and their public ip will be like "101.102.103.101, 101.102.103.102, 101.102.103.103 ... 101.102.103.200"

You should also create a GOLDEN_HOST which will be the base image for all of your vms and update the information about your GOLDEN_HOST in vmall.settings. Your GOLDEN_HOST's network should be configured as to be accessible by ssh from you main host and it should be shutdown before starting the provisioning process. In the provisioning process your golden host will be cloned, powered up accesed by ssh configured as a new vm and then rebooted in a loop. This way you will have as many vms as you like (currently up to 253) on a single host in an easy and automated way.

Hope this script helps you :)

Plesase feel free to customize or improve it and if you wish send me a merge reuqest.