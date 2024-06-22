# Farcaster Node Setup Guide

## Prerequisites

1. **Warpcast Account**: You need a Warpcast account. If you don't have one, you can sign up [here](https://warpcast.com/~/invite-page/488289?id=015f62b5) for $5.

2. **Server Requirements**:
    - 16GB RAM
    - 4 CPUs
    - 100GB storage

## Installation Steps

### 1. Update and Install Necessary Packages

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install screen -y
```

### 2. Start a Screen Session

```bash
screen -S warp
```

### 3. Install Docker

```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl start docker
sudo systemctl enable docker

sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

```

### 4. Run the Bootstrap Script

```bash
curl -sSL https://download.thehubble.xyz/bootstrap.sh | bash
```

### 5. Provide RPC URLs and Warpcast FID

During the bootstrap script execution, you will be prompted to enter:

1. ETH mainnet RPC URL: You can get it from [Infura](https://app.infura.io/dashboard) or [Alchemy](https://www.alchemy.com/).
   
2. OP Mainnet RPC URL: Similarly, get it from [Infura](https://app.infura.io/dashboard) or [Alchemy](https://www.alchemy.com/).

3. Warpcast FID number: You can find this by clicking on the three lines in the top right of your profile and then clicking the "About" button.

>   ![image](https://github.com/pvsairam/Farcaster/assets/9134015/f2361c11-a1c5-410d-ace7-aa11ee365e92)
>
>   ![image](https://github.com/pvsairam/Farcaster/assets/9134015/b7c5f0cc-32e4-4ccb-b689-8d1094ecbaac)


### 6. Monitor the Installation

After running the bootstrap script, you should see output indicating the progress. Initially, Snap will be installed, which may take some time. Once completed, you'll see an output similar to the image below.

[Image Loading...]


### 7. Detach the Screen Session

> To detach from the screen session, press Ctrl + A then D.


### 8. Monitoring with Grafana

You can monitor the node using Grafana. Access it via:

> http://SERVER-IP:3000

Replace SERVER-IP with the IP address of your server.

[Image Loading...]
