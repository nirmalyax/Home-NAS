# Raspberry Pi Home NAS System with Tailscale and Casa OS 🏡💾 

## Objective:

Build a robust Home NAS (Network Attached Storage) system using a Raspberry Pi, Tailscale, Next DNS for secure remote access, and Casa OS for a user-friendly interface.

## **Hardware Requirements:**

1. **Raspberry Pi:**
    - Model 3B or later for optimal performance.
    - Power supply.
    - MicroSD card (32GB recommended).
2. **External Storage:**
    - USB external hard drive or SSD for NAS storage.
3. **Network Connection:**
    - Stable internet connection for remote access.

## Step 1: Raspberry Pi Setup 🍓

### **1.1 Download and Install Raspberry Pi OS:**

- Visit the official Raspberry Pi website and download the Raspberry Pi OS.
- Use a tool like BalenaEtcher to write the OS image to a microSD card.

### **1.2 Boot Up Raspberry Pi:**

- Insert the microSD card into your Raspberry Pi.
- Connect the Raspberry Pi to a monitor, keyboard, mouse, and power supply.
- Power on the Raspberry Pi.

### **1.3 Enable SSH:**

- Open the Raspberry Pi Configuration tool using **`sudo raspi-config`**.
- Navigate to **`Interface Options`** and enable **`SSH`**.
- Save and exit.

### **1.4 Find Raspberry Pi's IP Address:**

- On the Raspberry Pi terminal, use the command **`hostname -I`** to find its IP address.

## Step 2: SSH RPI & Update and Upgrade🔄

```bash
ssh pi@<raspberry_pi_ip_address>
sudo apt update && sudo apt upgrade

```

## Step 3: Install Tailscale 🐾

- Install Tailscale by running the folowing script

```
curl -fsSL https://tailscale.com/install.sh | sh

```

## Step 4: Network Configuration 🔗

- Turn on IPv4 forwarding

```
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.conf

```

- Turn on IPv6 forwarding

```
echo 'net.ipv6.conf.all.forwarding = 1' | sudo tee -a /etc/sysctl.conf

```

- Re-execute the sysctl conf file

```
sudo sysctl -p /etc/sysctl.conf

```

- Login to Tailscale account

```bash
sudo tailscale up --advertise-exit-node

```

## Step 5: Tailscale Connection and NextDNS Integration 🌐

- Connect Tailscale with NextDNS for a secure gateway.

## Step 6: Install Casa OS 🏡

```bash
curl -fsSL <https://get.casaos.io> | sudo bash

```

## Step 7: Access Casa OS Remotely 🌐

- Casa OS is exposed on port 81.
- Access it from anywhere using the Raspberry Pi's IP address: `http://<raspberry_pi_ip_address>:81`.

## Step 8: NAS Setup 📁

- Configure your NAS by connecting external drives or creating shared folders.

🚀 Congratulations! Your Raspberry Pi is now a powerful Home NAS system with secure remote access through Tailscale and a user-friendly interface with Casa OS. Only authorized devices can access, ensuring your data is safe and secure.

Stay tuned for more tech adventures and smart home innovations! 🏡✨ #RaspberryPi #HomeNAS #Tailscale #CasaOS #TechMagic ✨💻
