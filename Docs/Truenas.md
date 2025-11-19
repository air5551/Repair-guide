# Introduction

> [!NOTE]
> This guide has been made for non-IT people
> it has a lot of words explaining the theory behind why things are done like this
> If you get stuck at a step just search the answer or contact me though
[the Issue tab](https://github.com/air5551/Repair-guide/issues)

## What is a NAS?

A NAS or network attached storage is like cloud storage but
instead of being in Icloud or Google Drive,
its a dedicated device designed to store data and
often for very long periods of time.
The way you access your data is though is almost the same.

## Boot Drive

The boot drive is where the actual operating system like Windows or MacOS.
Its main function in a NAS is to store things other then your data, like applications.

> [!IMPORTANT]
> the boot drive **CAN'T** be used as extra storage
Its recommanded to get an SSD with 128GB of storage like this [one](https://www.amazon.com/Silicon-Power-128GB-P34A60-SP128GBP34A60M28/dp/B09HMWH1DG/)
To disassemble the device follow this [Guide](Docs/Repair.md)

### The Operating system used

[TrueNAS](https://www.truenas.com/) is an Operating system designed solely
for NAS devices,
its free and perfect for this use. The interface can be quite daughting to people
but the guide will tell you how these things work

### Networking

By default all devices on your home network can't be accessed by the wider internet
one soluition is to do what is called port fowarding
but this gets really complicated.
[Tailscale](https://tailscale.com) is the simplist to set up and
it's very secure,
its like a private network that can accessed anywhere around the world
no one can access the NAS without your permission with this.

## Prerequisites

- An old laptop or desktop
- Storage drive that can connect to the laptop
- USB Drive, Preferibly over 8GB of storage
- *Optional* Ethernet Cable/Adapter, improves reliability

1. Download TrueNAS
Go to this [Download](https://www.truenas.com/download-truenas-community-edition/)
Skip the sign up prompt if you don't want the junk

2. Flash the USB drive

Documents
[text](https://www.disk-image.com/faq-bootmenu.htm)
