---
layout: post
title: Deploying EUC Images with Packer and Nutanix
permalink: "/deploying-euc-images-with-packer-and-nutanix/"
categories: [Citrix, Omnissa, VDI, DaaS, Automation, Packer, Nutanix, Prism Central]
description: Nutanix Builder v1.0.0 released and good to go for EUC image builds
image:
  path: /assets/img/deploying-euc-images-with-packer-and-nutanix/post_default_image.jpg
sitemap: true
hide_last_modified: true
comments: true
---

<!--excerpt-->

-  Table of Contents
{:toc}

## Intro to Packer and Nutanix

Packer has long been one of the go-to tools for automating Image builds across EUC environments. It's a simple solution to drive, which delivers consistent image builds across any supported platform.

Packer has one simple job: build you a ready-to-go image, zero touch. That’s its sole purpose in life.

Customers enjoy Packer for a multitude of reasons, one of the most appealing aspects, however, is to take your platform build processes away from your configuration components. This, when it’s boiled down, means you can ask Packer to build against many different platforms or clouds, but always have the same configuration applied to those images. Neat.

Nutanix has just dropped the [official v1.0.0 release of the Nutanix Builder](https://developer.hashicorp.com/packer/integrations/nutanix-cloud-native/nutanix/latest/components/builder/nutanix) for Packer, which has a huge amount of Windows on Nutanix focused enhancements, all of which benefit the EUC landscape when deploying on Nutanix.

The following important components have been implemented in the latest release (focusing purely on EUC use cases here, there are plenty of other goodies that have been dropped in this release as well):

-  Specify the number of cores vs socket-only configurations. Using the `core` parameter, you can now define the number of cores per socket. Very important for EUC builds, and while it doesn’t matter for the build process, it impacts the outputs (read on)
-  Support for Secure Boot, a hard dependency for Windows 11. The `boot_type` component now allows for a `secure_boot` block.
-  Support for vTPM additions, another hard dependency for Windows 11. You can now specify a `vtpm` block to add a vTPM.
-  Support for Windows Credential Guard has been added via the `hardware_virtualization` parameter.
-  Support for where your VM is built via the storage_container_uuid` parameter. This is handy if you don’t want to use the default container.
-  While not specific to this exact release, importantly, the `boot_wait` and `boot_command` options are what we use to allow you to boot from a stock standard Windows ISO and send in keystrokes to get past the "Press Any Key to Continue" boot message.

The above are all critical for getting a VM ready to go, but there have also been significant improvements to the outputs available and the artifacts left:

-  Using the `image_skip` parameter, you can now skip the creation of a Nutanix Image, which isn’t much use for EUC images (unless your integration with Nutanix uses images).
-  Using the `template` block, you now have a nice, clean Nutanix Template exported, ready for provisioning.
-  For those that can’t use Templates, and still use a Nutanix Snapshot with PE integration, there is a new `vm_retain` parameter that will keep the build VM, allowing you to move to PE and take whatever Snapshot you need of the Packer-built VM.
-  Using the `vm_clean` block, you can ask Packer to clean/remove any CD drives that were attached during the build, before any images or templates are created.

This is a huge release of Packer that enables our customers to continue using the same build tooling and processes against our platform, as they migrate towards us.

## Example Build - Windows 11 Enterprise 24H2

Below is a working source example, and the associated logic flow for creating a Windows 11 Enterprise VM on Nutanix using Packer. Note that our integration is with Prism Central.

This post doesn't cover setting up and using Packer, there are plenty of references out there, this is just showing the latest capabilities.

This template will create a Windows 11 24H2 template on Nutanix using Packer. It configures and actions the following:

-  Creates a VM with the specified resources (1 vCPU, 3 cores, 6144 MB memory) on the defined Nutanix cluster
-  Enables secure boot and adds vTPM
-  Enables Credential Guard (hardware_virtualization)
-  Attaches a NIC to the specified Nutanix subnet
-  Attaches a CD ROM and Boots from a stock Winows 11 ISO file
-  Attaches a Nutanix VirtIO ISO for driver installation
-  Attaches a disk of 60GB size on a specified storage container
-  Configures the boot priority to CD ROM
-  Waits 3 seconds after the intial boot and then sends the boot commands to skip the Windows "Press any key to boot from CD or DVD" prompt
-  Connects to the VM using WinRM on port 5985 with a timeout of 30 minutes
-  Removes all CD ROMs after the build is complete
-  Skips creating a Nutanix image, as a template will be used
-  Retains the VM after the build is complete for further testing or modifications (this is just to show how it works, you won't need this duing normal operations)
-  Creates a Nutanix template from the VM with a specified name and description

Note that this method uses an autounattend.xml file to automate the Windows installation including:

-  Adding the VirtIO drivers (from attached ISO)
-  Copying a SetupComplete.cmd script to run post-installation tasks such as enabling WinRM for Packer

Here is a cracking resource for getting started with [autounattend configuration files](https://github.com/StefanScherer/packer-windows/tree/main/answer_files) 

```
source "nutanix" "windows11" {
    nutanix_username    = var.nutanix_username
    nutanix_password    = var.nutanix_password
    nutanix_endpoint    = var.nutanix_endpoint
    nutanix_port        = var.nutanix_port
    nutanix_insecure    = var.nutanix_insecure
    cluster_name        = var.cluster_name
    os_type             = "Windows"
    communicator        = "winrm"
    cpu                 = 1
    core                = 3
    memory_mb           = 6144
    boot_type           = "secure_boot"
    boot_priority       = "cdrom"
    boot_wait = "3s" 
    boot_command = [
        "<spacebar><wait><spacebar><wait><spacebar><wait><spacebar><wait><spacebar><wait><spacebar><wait><spacebar><enter>"
    ]
    vtpm {
        enabled = true
    }
    hardware_virtualization = true
    vm_disks {
        image_type        = "ISO_IMAGE"
        source_image_name = "windows_11_business_editions_24h2_april_2025.iso"
    }
    vm_disks {
        image_type        = "ISO_IMAGE"
        source_image_name = "Nutanix-VirtIO-1.2.4.iso"
    }
    vm_disks {
        image_type              = "DISK"
        disk_size_gb            = 60
        storage_container_uuid  = "798df156-6472-4546-a784-283fa1d5c08d"
    }
    vm_nics {
        subnet_name       = "VLAN-10"
    }
    cd_files = [ 
        "files/autounattend.xml",
        "files/scripts/EnableWinRMforPacker.ps1",
        "files/scripts/SetupComplete.cmd"
    ]
    image_skip          = true
    vm_retain = true
    vm_clean {
        cdrom = true
    }
    template {
        create = true
        name = "Windows-11-Template-{{isotime}}"
        description = "Windows 11 Template Created by Packer"
    }
    winrm_port          = 5985
    winrm_timeout       = "30m"
    winrm_use_ssl       = false
    winrm_username      = var.winrm_username
    winrm_password      = var.winrm_password
}
```
