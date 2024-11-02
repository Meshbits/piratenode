---
layout: default
title: Setup Tor Node
nav_order: 8
---

# Setup Tor Node
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Install Tor service

To install Tor service execute the following commands:

```shell
sudo apt update
sudo apt -y install tor
```

# Configure Onion service for Pirate Node

Assuming that you have Pirate Chain node configred and running successfully, the next part is to configure the Onion/Tor service for Pirate Chain node. This means by the end of this guide, you will have a unique Tor `.onion` address for your home run Pirate Chain node which can be accesible world wide _**only through tor network**_ from any device.

{: .note }
It is also assumed that you are by now familiar to using command line file editor `nano`. If you are not either follow the previous sections to get idea or get help from Google or ChatGPT.

To edit the Tor service use the following comamnd:

```shell
sudo nano /etc/tor/torrc
```

{: .warning }
> DO NOT change any existing configuration in this file.
> 
> We are only adding our own configuraiton at the end of this file.

While in the edit mode of scroll down or use the arrow keys on your keyboard to go to the bottom of the file and paste the following lines:

```shell
# Directory holding the Pirate Chain Onion service configuration data
HiddenServiceDir /var/lib/tor/piratelightd/
# Mapping ports for Pirate Chain Light node to Onion service address
HiddenServicePort 9067 127.0.0.1:9067
HiddenServicePort 9068 127.0.0.1:9068
HiddenServicePort 80 127.0.0.1:80
```

The end of `torrc` file will look like the following screen-shot:

![](/assets/images/setup-tor-node/piratelightd-torrc-settings.png)

After this, save the file with keyboard shortcuts `CTRL+O`, then press `ENTER`, then press `CTRL+X` to exit, then press `ENTER`.

Expecting everything went smooth with this step, now restart the `Tor` service on this device and check it's status to make sure it is running fine.

```shell
sudo systemctl restart tor.service 
sudo systemctl status tor.service 
```

You will get output something like this from `status` commmand if it is running fine:


```shell
● tor.service - Anonymizing overlay network for TCP (multi-instance-master)
     Loaded: loaded (/lib/systemd/system/tor.service; enabled; preset: enabled)
     Active: active (exited) since Thu 2024-10-24 18:08:28 NZDT; 3s ago
    Process: 2633914 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 2633914 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Oct 24 18:08:28 piratenode.local systemd[1]: Starting tor.service - Anonymizing overlay network for TCP (multi-instance-master)...
Oct 24 18:08:28 piratenode.local systemd[1]: Finished tor.service - Anonymizing overlay network for TCP (multi-instance-master).
```


# Get Pirate Node Onion Service Info

Now that the Onion service is setup and confgiured, it's time to check the new onion service address which is mapped to the Light Wallet service on this device. For that just check if the onion service directory we configured in `torrc` is now created by the `Tor` Service upon restart or not.

```shell
sudo ls -lh /var/lib/tor/piratelightd/
```

You will get output something like this:

```shell
total 16K
drwx--S--- 2 debian-tor debian-tor 4.0K May  3 22:47 authorized_clients
-rw------- 1 debian-tor debian-tor   63 May  3 22:47 hostname
-rw------- 1 debian-tor debian-tor   64 May  3 22:47 hs_ed25519_public_key
-rw------- 1 debian-tor debian-tor   96 May  3 22:47 hs_ed25519_secret_key
```

You do not need to make any changes to any files in there.

{: .warning}
DO NOT share any `public_key` or `secret_key` data from this directory with anyone.

All you need to do now is to check what `.onion` address got generated by the `Tor` service which is mapped to your Pirate Chain Lightd server. For that use the following command:

```shell
sudo cat /var/lib/tor/piratelightd/hostname
```

This will print the `.onion` address on your command line terminal like the following example:

```
xklmtmi4x5ucxvc7ocwqtz6xbhrrbohx5fvj4ca3caqviwjt26ty6bqd.onion
```


# Test Pirate Node Over Tor Network
