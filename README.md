# Documentation

## See the full documentation on https://documentation-com.gitbook.io/pi-hole-installation/

# Prerequisites

## System Update

```bash
sudo apt update && sudo apt full-upgrade -y
```

## Curl Installation

```bash
sudo apt install curl -y
```

## Install Required Packages

```bash
sudo apt install apt-transport-https ca-certificates software-properties-common -y
```

## Docker Installation - Ubuntu

### **Add Docker APT Key**

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker.gpg
```

### **Add Docker APT Repository**

```bash
echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```

## Docker Installation - Debian

### **Add Docker APT Key**

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker.gpg
```

### **Add Docker APT Repository**

```bash
echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```

## **Install Docker**

```bash
sudo apt-get update
sudo apt-get install docker-ce -y
```

## **Download and Install Docker Compose**

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-Linux-x86_64" -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose
```

## Ansible Installation

```bash
sudo apt install ansible -y
```

# Pi-hole Docker Deployment

1. First we need to stop the DNS built in on the Ubuntu machine.

```bash
systemctl stop systemd-resolved
systemctl disable systemd-resolved
```

2. Next create a new directory named <mark style="color:red;">`pihole`</mark>and inside that directory create a <mark style="color:red;">`docker-compose.yml`</mark> file.

```bash
mkdir pihole
cd pihole
nano docker-compose.yml
```

3. After that populate the file with the information bellow, you can change the <mark style="color:red;">`WEBPASSWORD`</mark>.

```yaml
version: "3"

services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "80:80/tcp"
    environment:
      TZ: 'Europe/Lisbon'
      WEBPASSWORD: 'adminpassword'
    volumes:
      - './etc-pihole:/etc/pihole'
      - './etc-dnsmasq.d:/etc/dnsmasq.d'
    restart: unless-stopped
```

## Docker Compose

1. Start the WordPress deployment using docker-compose:

```bash
docker-compose up -d
```

2. After that navigate to the dashboard with <mark style="color:red;">`http://your_ip_address/admin`</mark> with the credentials of the <mark style="color:red;">`WEBPASSWORD`</mark>.
