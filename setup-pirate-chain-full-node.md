---
layout: default
title: Setup Pirate Chain Full Node
nav_order: 6
---

# Setup Pirate Chain Full Node
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Install Pirate Chain

You need to get the command line files for Pirate Chain, which will run on your Raspberry Pi machine, and download full copy of it's blockchain and keep it in synchronisation with the network. You can get the link to download command line files for Raspberry Pi from official website of Pirate Chain, or you can also get these directly from the source where they are released first. From the Github website, where the source code of Pirate Chain is updated and new builds/updates of Pirate Chain network command line tools are released. The direct link to the Pirate Chain's Github repository is:

[https://github.com/PirateNetwork/pirate](https://github.com/PirateNetwork/pirate){:target="_blank"}

You can head over to this address address from your local machine's web browser.

![](/assets/images/install-pirate-full-node/pirate-chain-git-repo.png)

On this page, click on the **latest** release link as marked in the screen shot.

Once you are on latest release page of Pirate Chain, make sure it shows `Latest` as marked on this next screen shot.

![](/assets/images/install-pirate-full-node/pirate-chain-releases.png)

On this page, scroll down to the section where it says **Assets**.

Under this section you are looking for:

1. An archive file, usually with the file extension `.zip` or `tar` or `tar.gz`. In this case, it is `.zip`.
2. The file name MUST consist `CLI` in it's name. WHich means the pirate chain tools are for command line only.
3. The file name MUST consist `aarch64` in it's name. Which means the pirate chain command line tools are only for the Raspberry Pi specific machine architecture.

The following screen shot gives the example of which file you are looking for under that section.

The number like `v5.8.2` is the version number of the latest Pirate chain command line tools. It will be little different, every time a new release is made available on Github repository of Piratet Chain.

![](/assets/images/install-pirate-full-node/pirate-chain-files-for-raspi.png)

Right click on this `.zip` file link and from the right click menu select whatever option allows you to copy it's link. It might show different phrase/line according to your OS and Web browser. Following is example from Google Chrome on MacOS:

![](/assets/images/install-pirate-full-node/pirate-chain-download-link.png)

Doing this you will have the direct link of the file copied. The URL will look like following:

```
https://github.com/PirateNetwork/pirate/releases/download/v5.8.2/pirate-cli-aarch64-v5.8.2.zip
```

You can use that now to download and setup Pirate Chain on your Raspberry Pi.




# Configure Pirate Chain Settings

Now you need to create a configuration file with settings for Pirate Chain.

First `SSH` into your Pirate Chain Node.

Then create the directories before creating the configuration file:

```shell
mkdir -p ~/.komodo/PIRATE
```

Now create and edit the configuration file with the following command:

```
nano ~/.komodo/PIRATE/PIRATE.conf
```

In configuration file copy/paste or type the following text:

```
rpcuser=SET_USERNAME_HERE
rpcpassword=SET_PASSWORD_HERE
rpcport=45453
server=1
txindex=1
rpcworkqueue=256
rpcallowip=127.0.0.1
rpcbind=127.0.0.1
addressindex=1
timestampindex=1
spentindex=1
```

NOTE: You need to replace the text `SET_USERNAME_HERE` and `SET_PASSWORD_HERE` with something. You can just put any random characters for it.

Once ready, press `CTRL + O` and hit `ENTER` key to save changes. And then press `CTRL + X` to exit the `nano` text editor.




# Configure Pirate Chain System Service

By now it is expected that you know your way around using `nano` editor. If you don't maybe readh through previous sections and you'll get the hang of it. For any troubles just google it and that should be easy enough to resolve.

In this section you are going to create a Pirate Chain System Service which will make sure the pirate chain node starts up whenever your Raspberry Pi device boots up.

File: `/etc/systemd/system/piratechain.service`


You need to create this new file at the location mentioned above.

You will also need to know the username under which you would want your pirate chain node be started under. Basically it is the same username that you are logged in as to this command shell over `SSH`. You can determin your username using this command:

```
whoami
```

If you been following this guide/documentation and had logged in using `ssh piratenode@piratenode.local` you will get the following output:

```
piratenode
```

Note down this **username** which you will need in next part of this guide.


To create the system service for pirate chain, use the following command:

```
sudo nano /etc/systemd/system/piratechain.service
```

You can copy/paste the following text contents in this file:

```shell
[Unit]
Description=PirateChain
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/pirated
Restart=always
RestartSec=5s
SyslogIdentifier=PirateChain
User=piratechain
Group=piratechain

[Install]
WantedBy=multi-user.target
```

In the above example I have used `piratechain` username for `User=` and `Group=`. If you had used different username, then make sure you update it in this file. Otherwise you will have issues starting pirate chain service on your device.

Expecting everything went well so far according to the above instructions provided, the next step to upgrade the system that there is a new system service, and make it start automatically on system boot up time. For that use the following comands:

```shell
sudo systemctl daemon-reload
sudo systemctl enable piratechain.service
```

Time to start the pirate chain service. For that use the following commands:

```shell
sudo systemctl start piratechain.service
```

If this comamnd execute successfully you will not get any output in command terminal. To check if the pirate chain service is running or not, you can use the `status` command like this:


```shell
sudo systemctl status piratechain.service 
● piratechain.service - PirateChain
     Loaded: loaded (/etc/systemd/system/piratechain.service; enabled; preset: enabled)
     Active: active (running) since Sun 2024-09-08 00:36:12 NZST; 1 month 16 days ago
   Main PID: 2031151 (pirated)
      Tasks: 21 (limit: 9259)
        CPU: 5h 40min 49.290s
     CGroup: /system.slice/piratechain.service
             └─2031151 /usr/local/bin/pirated
```

The above should be the output if pirate chain service is running on your device.

`Loaded: loaded (/etc/systemd/system/piratechain.service; enabled;` means that this service is set to automatically start on device boot up since it shows `enabled;`.

```shell
CGroup: /system.slice/piratechain.service
             └─2031151 /usr/local/bin/pirated
```

The above shows the pirate chain is running in background with `2031151`as it's process ID. If you do not see the process ID, and your output is something else, you are possibly having wrong config or some other issues. For now I'll not add the troubleshooting parts here, but over time can add them to this guide if needed. Until then Google and ChatGPT is your friend.

{: .note }
It is possible that after you execute the command `sudo systemctl status piratechain.service ` you get the blinking curose instead of yout getting back to the command line terminal like usual. In this case, juse press the key `Q` and you will exit from the output of the `status` command.


Congratulations! If you have came this far, that means you have a running Pirate Chain node on your Raspberry Pi device in your home! 👏 Good work!