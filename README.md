
# Kali Linux Environment Setup & Troubleshooting

## 🛠 Project Overview
A documented setup of a Kali Linux laboratory environment using VirtualBox 7.0. This lab is configured with a dual-adapter network architecture for secure, isolated penetration testing practice.

## 🚀 Technical Configuration
* **Hypervisor:** VirtualBox 7.0.x
* **Operating System:** Kali Linux (Debian 64-bit)
* **Network Adapter 1:** NAT (Internet Access/Updates)
* **Network Adapter 2:** Host-Only (Private Lab Network - 192.168.56.x)

## 🔧 Incident Log (Troubleshooting)
| Challenge | Root Cause | Resolution |
| :--- | :--- | :--- |
| **Missing .ova** | Source files provided as `.vbox`/`.vdi`. | Manually attached `.vdi` as a primary SATA drive. |
| **No Bootable Medium** | EFI boot was enabled by default. | Disabled **Enable EFI** in System settings. |
| **Network Interface Down** | `eth1` was uninitialized in the kernel. | Used `sudo ip link set eth1 up` to activate the Host-Only link. |
| **Default Credentials** | Security risk of using `kali/kali`. | Migrated user profile to custom administrative account `Naayomi`. |

## 📸 Lab Evidence
*(Images to be uploaded to the /images folder)*

## Implementation Walkthrough
1. Environment Virtualization
The first step was to create a "computer within a computer." I used Oracle VirtualBox 7.0 to act as a Hypervisor. This allowed me to allocate a specific portion of my laptop's physical hardware (RAM and Processor cores) to an isolated guest environment.

2. Operating System Deployment
I deployed Kali Linux, a specialized, Debian-based operating system used for security auditing.

The Challenge: The source files were provided as a Virtual Disk Image (.vdi) rather than a standard one-click installer.

The Action: I manually constructed the virtual hardware profile and "hooked" the digital hard drive into the system's virtual SATA controller.

3. System Boot Configuration
Newer virtualization software often attempts to start a system using a modern "language" called EFI. However, the specific version of Kali I used required a legacy boot method.

The Action: I accessed the virtual motherboard settings and disabled the EFI option. This allowed the system to recognize the boot files and start the operating system successfully.

4. Isolated Network Architecture
To ensure a safe environment, I configured two distinct network pathways (Adapters):

Internet Pathway (NAT): This allows the VM to reach the internet to download security updates without exposing the rest of my home network.

Internal Laboratory Pathway (Host-Only): I created a private, digital "cable" between my physical laptop and the virtual machine. This ensures that any security tests I run remain trapped within this private link and never leak onto the real internet.

5. System Hardening & Identity Migration
Standard installations come with "factory default" usernames and passwords, which is a significant security risk.

The Action: I performed a system-wide update to patch all software. I then used administrative commands to migrate the entire user profile from the default "kali" account to a custom identity, Naayomi. This included renaming the home directories and updating group permissions to ensure full administrative control was tied to a unique, secure identity.
