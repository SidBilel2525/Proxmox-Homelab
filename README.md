# 🖥️ My Proxmox Homelab
Building Proxmox Homelab on lenovo ThinkCentre

## :mag: Project Overview

**Status:** Planning

I’m building a homelab so I can manage my Lenovo ThinkCentre from anywhere through a browser. My goal is to open my own domain over HTTPS, verify my identity, and sign in to the Proxmox dashboard from outside my home network.

This first project runs directly on the ThinkCentre. Hosting a WordPress website on an Ubuntu Server VM will be a separate project.
ddd
## Hardware and software

| Component | Planned setup |
| --- | --- |
| Host | Lenovo ThinkCentre Tiny, listed as an M720q with an Intel Core i5-7400T |
| Memory and storage | 8 GB DDR4 and a 256 GB SSD |
| Network | Wired Gigabit Ethernet |
| Hypervisor | Proxmox VE installed on the SSD |
| Remote access | A custom subdomain, Cloudflare Access, and Cloudflare Tunnel |

## NetWork Layout

I’ll connect the ThinkCentre to my home network over Ethernet. On the LAN, I’ll manage it through the Proxmox HTTPS interface on port 8006.

Away from home, I’ll open a hostname such as `pve.example.com` in a browser. Cloudflare Access will check my identity before sending the request through a tunnel to Proxmox. The tunnel connector will run on the ThinkCentre and connect outward, so I can leave inbound port 8006 closed on my router.

## Installation and configuration

- [ ] Verify the hardware and back up files on the SSD before installing Proxmox.
- [ ] Create the Proxmox VE installer USB, boot the ThinkCentre from it, and install the hypervisor.
- [ ] Configure its management address and sign in from my main PC over the LAN.
- [ ] Set up my domain in Cloudflare DNS and choose a subdomain for Proxmox.
- [ ] Create a Cloudflare Access policy that allows only my identity and requires multifactor authentication.
- [ ] Install the tunnel connector on the host and route the subdomain to the Proxmox HTTPS interface with certificate verification enabled.
- [ ] Configure SSH key authentication for terminal access from my main PC on the LAN.

## References

- [Proxmox VE ISO Installer — official download](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso)
- [Proxmox VE installation guide](https://www.proxmox.com/en/products/proxmox-virtual-environment/get-started)
- [Homelab tutorial playlist on YouTube](https://www.youtube.com/playlist?list=PLSuzYIVSEUT4Vcb1DHW6xGvGcm5zci13N)

## Testing and Results

| Test | What I expect to see | Result |
| --- | --- | --- |
| Local management | From my main PC, I can sign in and open the node’s Summary page. | Pending |
| Remote browser access | I can open my domain over HTTPS without a certificate warning, authenticate, and reach the Summary page. | Pending |
| Access restriction | In a fresh private browser session, I must pass the Cloudflare identity check before I can reach the Proxmox login page. | Pending |
| SSH access | From my main PC, I can open a terminal session on the ThinkCentre using my SSH key. | Pending |

## Troubleshooting and Lessons Learned

As I build the lab, I’ll record any issue I encounter, the test that helped me identify its cause, and how I confirmed the fix. After the remote-access test, I’ll add a screenshot of the Summary page and note which device and network I used.
