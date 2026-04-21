# Kali-Linux-Virtual-machine-set-up
A step-by-step documentation of setting up a Kali Linux Virtual Machine on Windows using VirtualBox.

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
