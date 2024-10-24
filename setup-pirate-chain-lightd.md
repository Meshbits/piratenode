---
layout: default
title: Setup Pirate Chain Lightd Service
nav_order: 7
---

# Setup Pirate Chain Lightd Service
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Pirate Lightd Prerequisites

 1. **Local Pirate Chain node synced 100% with the network:** If you have followed this guide, this must have been already done.
 2. cURL, Git
 3. Go Language compiler

# Install cURL and Git

Just execute the following command in your `SSH` terminal:

```shell
sudo apt update
sudo apt -y install curl git
```

# Install Golang

After login to your Pirate Chain Node's `SSH` terminal execute the following comamnds:

```shell
wget https://go.dev/dl/$(curl -s https://go.dev/VERSION?m=text | head -n 1).linux-arm64.tar.gz
sudo rm -rf /usr/local/go && tar -C /usr/local -xzf $(curl -s https://go.dev/VERSION?m=text | head -n 1).linux-arm64.tar.gz
```

The above commands will download and install Go Language compiler on your device.

Next check if Golang is setup in system path or not, and if it's not found in the system path, then add it.

Execute the following command:

```shell
cat $HOME/.profile | grep /usr/local/go/bin
```

If this output is blank then execute this next command, otherwise skip this setep:

```shell
echo 'PATH=$PATH:/usr/local/go/bin' >> $HOME/.profile
```

Now just to make sure it is setup execute this command which which shuld now print the output instead of blank output:

```shell
cat $HOME/.profile | grep /usr/local/go/bin

# OUTPUT
PATH=$PATH:/usr/local/go/bin
```

If you got the output as shown in the above example then referesh your `SSH` session with updated settings and verify the if you are able to execute `go` commands:

```shell
source $HOME/.profile
go version

#OUTPUT
go version go1.23.2 linux/arm64
```

If you see the output of `go version` commmand that means your system is setup with golang perfectly. On to the next step.

# Install Pirate Chain Lightd

In your `SSH` terminal execute the following commands:

```shell
cd $HOME
git clone https://github.com/PirateNetwork/lightwalletd.git --branch  dev
cd lightwalletd
go build
```

This should download the `lightwalletd` service, and build it on your local device. Now check if the command `lightwalletd` is there.

```shell
cd $HOME/lightwalletd
ls -lh lightwalletd
-rwxr-xr-x 1 piratechain piratechain 20M Oct 24 19:07 lightwalletd
```

If `ls` command prints the `lightwalletd` file is built successfully. Now execute the next command which will help execute the `lightwalletd` with little easier in future.

```shell
sudo ln -s $HOME/lightwalletd/lightwalletd /usr/local/bin/
ls -lh /usr/local/bin/lightwalletd

#OUTPUT
lrwxrwxrwx 1 root root 40 May  6 12:59 /usr/local/bin/lightwalletd -> /home/satinder/lightwalletd/lightwalletd
```

If the above command prints output to your command line terminal everything is OK for next steps to proceed.

# Congfigure Pirate Chain Lightd



# Setup Pirate Chain Lightd System Service

