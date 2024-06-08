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

# Configure Pirate Chain System Service

