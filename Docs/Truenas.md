
# Introduction

> [!NOTE]
> This guide has been made for non-IT people
> it has a lot of words explaining the theory behind why things are done like this
> If you get stuck at a step just search the answer or contact me though
[The Issue tab](https://github.com/air5551/Repair-guide/issues)

<details>
    <summary> An introduction on storage Units (Skip if you know how they work) </summary>
So A normal photo you take is usually 4.5MB
Now so in a 500GB harddrive there could be about 111,111 photos in that harddrive

There is a mental shortcut when going from Megabytes(MB) to Gigabytes(GB) to Terabytes(TB)
Its just multply by 1000 to go up like 1000GB is 1TB or 1000MB are in 1GB

</details>

## What is a NAS?

A NAS or network attached storage is like cloud storage but instead of being in
Icloud or Google Drive, its a dedicated device designed to store data
and often for very long periods of time.
The way you access your data is though is almost the same.

### Boot Drive

The boot drive is where the actual operating system like Windows or MacOS.
Its main function in a NAS is to store things other then your data, like applications.

> [!IMPORTANT]
> the boot drive **CAN'T** be used as extra storage
Its recommanded to get an SSD with 128GB of storage like this
[one](https://www.amazon.com/Silicon-Power-128GB-P34A60-SP128GBP34A60M28/dp/B09HMWH1DG/)
> Also **ALL** the data on that disk will be wiped make sure
that there is **NOTHING** important

### The Operating system used

[TrueNAS](https://www.truenas.com/) is an Operating system designed
solely for NAS devices,
its free and perfect for this use. The interface can be quite daughting to people
but the guide will tell you how these things work

### Networking

By default all devices on your home network can't be accessed by the wider internet
which is a good thing
one soluition is to do what is called port fowarding but this gets really
complicated and might not be possible.
[tailscale](https://tailscale.com) is the simplist to set up and it's very secure,
its like a private network that can accessed anywhere around the world,
the only requiement is to be connected to the internet.

## Prerequisites

- An old laptop or desktop
- Storage drive that can connect to the laptop
- USB Drive, Preferibly over 8GB of storage
- *Optional* Ethernet Cable/Adapter, improves reliability

### 1. Download TrueNAS

Go to this [Download Page](https://www.truenas.com/download-truenas-community-edition/)


Skip the sign up prompt if you don't want the junk

### 2. Flash the USB drive

Flash the USB drive using [Balena etcher](https://etcher.balena.io/)

 ![Balenaetcher Main screen](Images/Balenaetcher-main.png)
 Select the file you downloaded it's a .iso file
 it goes like this but the version will change
 then make sure that the USB drive is plugged in
 just hit flash after
 TrueNAS-SCALE-25.04.2.5.iso


### 3. Plug in the USB drive into the Laptop/Desktop

- Poweroff the laptop completely
- Power on the device but constantly press the Bootmenu key,

if you don't know search in this [list](https://www.disk-image.com/faq-bootmenu.htm)
> [!NOTE]
> Often the mouse will not work in this menu so use the arrow keys to navigate this

<details>
<summary> Did you get a Security violation screen/Secureboot? </summary>
Search the same list for your bios key
again the mouse may not work
Then search the menus for security or something like that
last resort is to search

```text
How to disable secureboot on (Laptop/Desktop) 
```

If your using a desktop, search the motherboard maker (etc. Acer, Asrock, Asus)
their logo should always display when you boot the device

</details>

4. TrueNAS installer menu

> [!NOTE]
> The mouse will not work
> Use the arrow keys and press enter to get threw the menus




5. First Boot

Wait for the device to boot


