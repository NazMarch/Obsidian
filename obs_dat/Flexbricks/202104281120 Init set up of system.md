#flexbricks 

1. Install Ubunty
2. Install Vbox:
3. Clone windows VB files
4. Create virtual machine

Virtual Machine set up:

System: 
- Motherboard: 5000MB Base memory, Boot order: Hard disk only, chipset - PIIX3, Point device - USB tablet, Extended Features - Enable I/o APIC
- Processor: processors - 3, execution cap - 100%, extended features - Enable PAE/NX 
- Acceleration: HYPER -V, Enable nested paging = true

Display:
- Screen: Video memory - 128 MB, Monitor Count - 1, Graphics controller - VBoxSVGA, ==Acceleration: Enable 3D Acceleration = false ==
- Other tabs: false
- Acceleration: ==FALSE==

Storage:
- Storage devices: 
	-  Controller - IDE, type: PIIX3, use host I/O Cache
		- Yunique2020.vdi: Attributes, IDE  Primary I, Solid-state=false
		- ==Enabled   ISO discs ==

Shared Folders: 
- Installed shared folder: chosen folder path, Auto-mount = true, Mount point: "S:"

From Ubuntu select shared folder in props: Give access to file changes

```ad-danger
title: Error while pull
```bash
git pull origin develop

# if got error:
# RPC failed
# result = 56
# HTTP code = 200MiB
# fatal: early EOF
# the remote and hung up unexpected edly
# fatal: index-pack failed


# DO: 
git config --global http.postBuffer 2M
git pull origin develop
```



