---
layout: post
title: Visual Studio Code on Ubuntu 15.04
description: |
    In this post I provide a "by the seat of your pants" no-frills guide to getting Visual Studio Code up and running on [Ubuntu](http://www.ubuntu.com/).
---

In this post I provide a "by the seat of your pants" no-frills guide to getting
[Visual Studio Code](https://code.visualstudio.com/)
up and running on
[Ubuntu](http://www.ubuntu.com/).

## Ubuntu GNU/Linux 15.04 64-bit on Virtual Box

Follow these instructions to install Ubuntu GNU/Linux 15.04 64-bit on Virtual Box. If you already have a Linux box you want to use you can skip this step.

1. Download and install
[Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads).

2. Download the ISO for
[Ubuntu Desktop GNU/Linux 15.04 64-bit](http://www.ubuntu.com/download/desktop).

3. Create a new VM using the _Linux => Ubuntu (64 bit)_ template.

    i. I suggest a minimum of 2GiB of RAM and a maximum of half of your host memory (e.g. my desktop has 16GiB of RAM so I'll allocate 4GiB of RAM).

    > You can always dial it up or down later!

    ii. I suggest you use a _dynamically allocated_ disk of a large enough "virtual size" so you won't have to resize it in the future.

    > I'm using a 64GiB disk ;)

    iii. If you know your VMs then you can tweak all the VM settings like I do.
    If you're not comfortable doing that then just leave them "as is" and everything should work fine.

4. Mount the ISO against the VM you just created and "power on" the VM.
You should see a screen like the following (if everything is working correctly).
![GNU GRUB]({{site.baseurl}}public/images/posts/2/grub.png "GNU GRUB")

5. Select the _Install Ubuntu_ option and follow the prompts.
If you get stuck check out the
[install guide](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop).

> Don't forget to install the _VirtualBox Guest Additions_ after installing Ubuntu and booting up for the first time.

## Prerequisites

It turns out there are a lot of things you need to do before you can open [Visual Studio Code](https://code.visualstudio.com/) on [Ubuntu](http://www.ubuntu.com/) and start coding.

> This section is based on
[ASP.NET 5 and DNX guide on GitHub](https://github.com/aspnet/home).

### Update Ubuntu

Make sure your [Ubuntu](http://www.ubuntu.com/) is up to date (has up to date packages) by opening a _Terminal_ and running `sudo apt-get update && sudo apt-get upgrade` now.

### Mono

The version of
[Mono](http://www.mono-project.com/)
(3.2.8) that ships with
[Ubuntu 15.04 (Vivid Vervet)](http://releases.ubuntu.com/15.04/)
is not new enough for
[ASP.NET 5](http://www.asp.net/vnext)
(we need 4.0.1 or newer).

Run the following commands to install
[Mono](http://www.mono-project.com/)
4.0.1:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
```

```
echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list
```

```
sudo apt-get update && sudo apt-get install mono-complete
```

### Node.js, NPM and Build Essential

Install
[Node.js](https://nodejs.org/) + the related
[Node Package Manager (NPM)](https://www.npmjs.com/) and
[Build Essential](https://packages.debian.org/jessie/build-essential)
by running `sudo apt-get install nodejs npm build-essential` now.

> _Build Essential_ may be required to build native extensions for _Node_ modules.

### libuv

[libuv](https://github.com/libuv/libuv)
is required by the
[Kestrel Http Server](https://github.com/aspnet/KestrelHttpServer)
that we will use to host our web applications.

Run the following commands to build, install and configure
[libuv](https://github.com/libuv/libuv)
1.4.2:

```
sudo apt-get install automake libtool curl
```

```
curl -sSL https://github.com/libuv/libuv/archive/v1.4.2.tar.gz | sudo tar zxfv - -C /usr/local/src
```

```
cd /usr/local/src/libuv-1.4.2
```

```
sudo sh autogen.sh
```

```
sudo ./configure
```

```
sudo make
```

```
sudo make install
```

```
sudo rm -rf /usr/local/src/libuv-1.4.2 && cd ~/
```

```
sudo ldconfig
```

TODO: continue on from here...
