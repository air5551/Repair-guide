
# Introduction



> [!NOTE]
> This guide has been made for non-IT people
> it has a lot of words explaining the theory behind why things are done like this
> If you get stuck at a step just search the answer or contact me though
> Also as of writing this (Dec 2025) RAM and likely SSD prices have
> Skyrocketed and are not expected to come down in 12-18 Months
[The Issue tab](https://github.com/air5551/Repair-guide/issues)


<details>
    <summary> An introduction on storage Units (Skip if you know how they work) </summary>
So A normal photo you take is usually 4.5MB \
Now so in a 500GB harddrive there could be about 111,111 photos in that harddrive\

There is a mental shortcut when going from Megabytes(MB) to Gigabytes(GB) to Terabytes(TB)\
Its just multply by 1000 to go up like 1000GB is 1TB or 1000MB are in 1GB

</details>

## What is a NAS?

A NAS or network attached storage is like cloud storage but instead of being in 
Icloud or Google Drive, its a dedicated device designed to store data
and often for very long periods of time. \
The way you access your data is though is almost the same.


### Boot Drive

The boot drive is where the actual operating system like Windows or MacOS.\
Its main function in a NAS is to store things other then your data, like applications.\

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
- Storage drive that can connect to the device
- USB Drive, Preferibly over 8GB of storage
- *Optional* Ethernet Cable/Adapter, improves reliability

### 1. Download TrueNAS

Go to this [Download Page](https://www.truenas.com/download-truenas-community-edition/)


Skip the sign up prompt if you don't want the junk

### 2. Flash the USB drive

Flash the USB drive using [Balena etcher](https://etcher.balena.io/)

![img](/Images/Balenaetcher-main.png)


 Select the file you downloaded it's a .iso file 
 
 it goes like this but the version will change
 then make sure that the USB drive is plugged in
 just hit flash after
 TrueNAS-SCALE-25.04.2.5.iso


### 3. Plug in the USB drive into the Laptop/Desktop

- Poweroff the device completely
- Power on the device but constantly press the Bootmenu key,

if you don't know search in this [list](https://www.disk-image.com/faq-bootmenu.htm)
> [!NOTE]
> Often the mouse will not work in this menu so use the arrow keys to navigate this
> Although Dell and HP devices tend to have mouse support



<details>
<summary> Did you get a Security violation screen/Secureboot? </summary>
Search the same list for your bios key
again the mouse may not work
Then search the menus for security or something like that
last resort is to search

```text
How to disable secureboot on (Laptop/Desktop) 
```

If your using a desktop, search the motherboard maker (etc. MSI, Asrock, Asus)
their logo should always display when you boot the device

</details>


### 4. TrueNAS installer menu



> [!NOTE]
> The mouse will not work
> Use the arrow keys and press enter

Press enter here 

![Img](/Images/Screenshot_20251206_170012.png)

Use the spacebar to select a drive
![Img](/Images/Screenshot_20251206_170151.png)

SSDs often show up like sda or nvme0n1

But this depends on the type of drive used

Restart the device after this is done on the installer menu


### 5. First Boot and Accessing the webUI

Wait for the device to boot.

This may take about 5 minutes depending on hardware


Enter in the address shown with the
http://

Its not required to put the http:// part

Example
![img](/Images/IP-Addresses.png)

### 6. TrueNAS Storage configuration

Go to the Storage Tab \
![img](/Images/Screenshot_20251206_170929.png)

Create a Storage pool \
![img](/Images/Screenshot_20251206_171445.png)

> [!NOTE]
> Its **Highly** recommanded to use 2 drives in a mirror configuration
> Instead of this
> Also note that the two drives should be the same capacity (ex. 500GB and 500GB SSDs)

After this press "Save and go to review" then save the drives





<details open>
    <summary> Tailscale setup </summary>

Signup for tailscale [Here](https://login.tailscale.com/start)

Download the tailscale apps [here](https://tailscale.com/download/mac)

Once your logged and setup, you should be on this screen \
![img](/Images/Tailscale.png)

</details>

### 7. TrueNAS-tailscale setup

Get a Tailscale Auth key [here](https://login.tailscale.com/admin/settings/keys)
Copy it, its going to be used Balenaetcher

> [!NOTE]
> Treat these like passwords

Go to the apps menu
![img](/Images/Apps.png)

Click on 'discover apps'

then search tailscale
then press install

Insert the Auth key

![Img](/Images/Tailscale-TrueNAS.png)

Then just press install, The tailscale admin panel

will show the device as being "Connected" when its ready


### 8. Remote Access


> [!WARNING]
> Windows/SMB shares should **NOT** be used if possible
> They are insecure[^1],slow
> and a nightmare to configure on TrueNAS

Go back to the apps menu
Then discover apps 

Search "webDAV"

Press install

> [!IMPORTANT]
> Using the default Authencation type
> Can expose your files to everyone on the Wifi network could access
> the files with the proper tools
> Keep in mind these security risks, Otherwize use basic Auth




### 9. Further Reading and WebDAV Clients

> [!IMPORTANT]
> Before starting make sure that **ALL** devices
> that are entended to connect to the NAS
> have tailscale configured and running


So On clients, I can't reasonably make a client guide due to the variation/OS diffrences
but all of them do follow some basic ideas (Or should)

When entering in a Tailscale URL, it should always be copied because
tailscale does put a mysterious string like tail(A random ID) here
like truenas.tail03b6h5.ts.net, It can be copied though the tailscale admin panel
or a client device

Tailscale URLs always start with Hostname.tail(A random id).ts.net
like truenas.tail03b6h5.ts.net, they can be copied with the admin console by clicking
on the 100.x.y.z address then copying the .ts.net address

The WebDAV server URL will be diffrent from the trueNAS adminUI entered in
step 5

### Security

If your hyperpranoid about some evil hackers trying to compromise your NAS
you really shouldn't be worried, if the systems kept up to date.

#### About Tailscales Security

Everything sent accross it is end-to-end encrypted
meaning that only your device and the NAS can see your data
not even tailscale can see your traffic, if the data is captured in transit,
tts only going to look like a garbled mess.
This is one of the reasons why I did not use a VPN server for this guide.
They tend to be complex and ISPs (Like comcast) block VPN traffic on their own hardware
Security tends to be a nightmare because the data isn't fully end-to-end encrypted

For more details [See tailscales explaination on "Zero Trust Networking"](https://tailscale.com/kb/1123/zero-trust)


[TrueNAS Refrences and More explaination on how things are done](https://www.truenas.com/docs/references/)




[^1]:[More info here](https://en.wikipedia.org/wiki/EternalBlue#Details)







