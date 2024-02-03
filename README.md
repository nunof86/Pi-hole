# Prerequisites

## System Update

```bash
sudo apt update && sudo apt full-upgrade -y
```

## Install Required Packages

```bash
sudo apt install apt-transport-https ca-certificates software-properties-common -y
```

## Docker Installation - Ubuntu

### **Add Docker APT Key**

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### **Add Docker APT Repository**

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Docker Installation - Debian

### **Add Docker APT Key**

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### **Add Docker APT Repository**

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
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
