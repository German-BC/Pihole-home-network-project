# Pihole-home-network-project
## Pi-hole Home Network Ad Blocking Project
### Overview

This project sets up and configures Pi-hole on a Raspberry Pi to provide network-wide ad blocking and DNS filtering. The Raspberry Pi is assigned a static IP address and configured so that the home router uses it as the primary DNS server.

### Hardware Used
- Raspberry Pi 5 (8GB)
- Official Raspberry Pi OS (Bookworm, 64-bit)
- Ethernet connection to home network

### Key Steps Completed

1. Perform initial Raspberry Pi setup and set a user account.
2. Enable SSH, either during imaging or using ```sudo raspi-config``` from a terminal.
3. Update the system: <br>```sudo apt update && sudo apt upgrade -y```
4. Install Pi-hole using the official script: <br>```curl -sSL https://install.pi-hole.net | bash```
5. Assign a static IP address via the router's DHCP reservation settings:
   - Log in to the router's admin settings page.
   - Find the Pi under connected devices.
   - Reserve its LAN IP (to ensure its address remains consistent without configuring it on the Pi)
6. In the router DNS settings, set Primary DNS to the Pi-hole IP.
   - Optional: Add a Secondary DNS set to 0.0.0.0 to force all devices to use Pi-hole.
  
### Result

All devices on the home network now use DNS-level ad and tracking blocking. Additional device-level blockers (like uBlock Origin) can enhance results.

### Future Improvements

- Add Unbound for local recursive DNS to keep network independent of 3rd-party DNS providers
- Add Tailscale for secure remote access to home network
- Add PiVPN for secure personal VPN (WireGuard/OpenVPN)

## NOTES

### Why Use DHCP Reservation Instead of Static IP on the Pi?

Assigning a static IP in the router ensures that:
- The IP remains consistent even after reboots
- The router is always aware of the device's IP assignment
- Avoids potential IP conflicts if the router DHCP range changes
