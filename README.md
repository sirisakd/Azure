# Azure-CLI 2.0

## Install Ubuntu terminal

First we need to activate "Windows Sub-system for Linux" (WSL) via PowerShell (reboot required)

```{Syntax language, PowerShell}
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Then install the terminal

```{Syntax language, PowerShell}
lxrun /install
```

The terminal is now available

## Update Ubuntu

```{Syntax language, Shell}
sudo apt update && sudo apt upgrade
```

## Install Python 3.6 (this specific version is needed for Azure CLI)


## Install Azure CLI

### Pre requisite packages

#### Python 3.6

```{Syntax language, Shell}
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt update
sudo apt install python3.6
```

#### Azure-cli dependencies

```{Syntax language, Shell}
sudo apt-get install apt-transport-https lsb-release software-properties-common dirmngr -y
```

#### Azure-cli repository

Source list

```{Syntax language, Shell}
AZ_REPO=$(lsb_release -cs)
echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    sudo tee /etc/apt/sources.list.d/azure-cli.list
```
Gpg Key

```{Syntax language, Shell}
sudo apt-key --keyring /etc/apt/trusted.gpg.d/Microsoft.gpg adv \
     --keyserver packages.microsoft.com \
     --recv-keys BC528686B50D79E339D3721CEB3E94ADBE1229CF
```

### Install Azure-cli

This step will be very long due to the number of object to unpack

```{Syntax language, Shell}
sudo apt-get update
sudo apt-get install azure-cli
```
