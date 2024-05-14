---
layout: default
title: Connecting to Pirate Node
nav_order: 4
---

# Connecting to Pirate Node
{: .no_toc }
In this section we will connect to our Pirate Node device over network through command line.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Command Line Terminal
You have to use a command line terminal according to the Operating System you are running.

- **For Windows:** [PuTTY](https://www.putty.org/){:target="_blank"}
- **For Linux:** Just use `Terminal` application. Just search in specific Linux distribution's Terminal Application, and you must be good to go.
- **For MacOS:** Search `Terminal` application, and you must be good to go.

# Ping Pirate Node
You can use `ping` command to test if Pirate Node is accessible over your local network.

```bash
ping piratenode.local
ping piratenode.local 
PING piratenode.local (192.168.1.45): 56 data bytes
64 bytes from 192.168.1.45: icmp_seq=0 ttl=64 time=12.295 ms
64 bytes from 192.168.1.45: icmp_seq=1 ttl=64 time=9.951 ms
64 bytes from 192.168.1.45: icmp_seq=2 ttl=64 time=10.405 ms
64 bytes from 192.168.1.45: icmp_seq=3 ttl=64 time=14.383 ms
^C
--- piratenode.local ping statistics ---
4 packets transmitted, 4 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.951/11.759/14.383/1.752 ms
```

It will keep printing the output like above.

To cancel or exit: Press `CTRL+C` on keys on your keyboard.

If you are able to see an IP address in the `ping` output, it means your Pirate Node is accessible over network.


# Connecting to Pirate Node with SSH
Now that we are sure it is accessible, let's connect to it with `SSH` commmand using the `Terminal` application.

For this command it is assumed the `username` and `password` you setup in previous section for SSH is `piratenode`. If you have used different `username` and/or `password` please use that accordingly in the `SSH` command.

Type in the following command in your `Terminal` application:

```bash
ssh piratenode@piratenode.local
```

Just for the first time connection, it will show the following output and ask you to type your input:

```bash
ssh piratenode@piratenode.local
The authenticity of host 'piratenode.local (192.168.1.45)' can't be established.
ED25519 key fingerprint is SHA256:rQHONg+K67Yhh5BJE9rXriTplGGcN/j4Kah5BAdC4B4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
```

Just type `yes` and press `ENTER` on your keyboard.

Next it will ask you to type in the `password`. Use the same password you created at the time of making the microSD card from **OS Customisation** section.

```bash
Warning: Permanently added 'piratenode.local' (ED25519) to the list of known hosts.
piratenode@piratenode.local's password: 
```

Once you are connected you will see the following output:

```bash
Linux piratenode.local 6.6.28+rpt-rpi-2712 #1 SMP PREEMPT Debian 1:6.6.28-1+rpt1 (2024-04-22) aarch64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu May  9 21:48:27 2024 from fdf1:f4e4:a15c:5c4f:1c28:9920:d3db:448
piratenode@piratenode:~ $ 
```

If you see `piratenode@piratenode:~ $ ` that just means you are successfully connected to your Pirate Node through command line. Well done if you have made this far without much issues! 👏


# Alternative Links

This seems good resource to check for alternative guide on how to connect to SSH server.
- [How to Connect to an SSH Server from Windows, macOS, or Linux](https://www.howtogeek.com/311287/how-to-connect-to-an-ssh-server-from-windows-macos-or-linux/){:target="_blank"}

