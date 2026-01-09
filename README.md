# Headless IoT Security Node  
**USB RNDIS • Headless Provisioning • Secure SSH Access**

This repository documents a real-world **headless IoT device deployment and troubleshooting workflow**, focused on USB-based networking (RNDIS), IP validation, and secure SSH onboarding.

The goal is to demonstrate how small IoT devices can be securely brought online **without a screen, keyboard, or Wi-Fi**, using only a USB connection and proper host-side validation.

---

## What this project demonstrates

- Headless device provisioning (no monitor / no keyboard)
- USB Gadget Mode networking (RNDIS / USB Ethernet)
- Windows host network validation
- IP addressing and ARP discovery
- Secure SSH onboarding behavior on modern Linux images
- System-level service validation on embedded devices

This project reflects **real troubleshooting**, not a happy-path tutorial.

---

## Lab environment

### Host system
- Windows 11
- PowerShell used for validation:
  - `ipconfig`
  - `arp -a`
  - `ping`
  - `ssh`
- USB Ethernet / RNDIS Gadget driver

### Device
- Raspberry Pi Zero 2 W–class hardware
- Linux-based headless image
- systemd-managed services
- OpenSSH enabled

---

## Network architecture (USB-only)

Windows Host
USB Ethernet (RNDIS)
IP: 10.0.0.1
|
| USB cable
|
IoT Device
USB Gadget Ethernet
IP: 10.0.0.2
> ⚠️ “No Internet access” on the USB adapter is **expected** in a direct host-to-device setup.

---

## Validation workflow

### 1. Confirm USB Ethernet detection (Windows)
- Device Manager → Network adapters
- Verified presence of **USB Ethernet / RNDIS Gadget**
- Link status: **Up**

---

### 2. Confirm host IP assignment
```powershell
ipconfig

Expected:
	•	Host receives an IP on the USB Ethernet interface
Example: 10.0.0.1

⸻

3. Confirm Layer 2 discovery (ARP)
arp -a

Expected:
	•	Device appears in ARP table after traffic
	•	Example entry:

10.0.0.2  <device-mac>  dynamic

4. Confirm Layer 3 connectivity
ping 10.0.0.2
Expected:
	•	Successful replies
	•	0% packet loss

SSH access validation

ssh pi@10.0.0.2

Observed behavior:
	•	Initial warning that SSH may not work until a valid user is configured
	•	This is intentional security hardening on modern images
	•	After user/password setup, SSH access succeeds

Successful login confirms:
	•	Network stack is operational
	•	SSH daemon is running
	•	Device is fully reachable headlessly


Security takeaway

Modern embedded Linux images often block SSH access until first-boot user configuration is complete.

This prevents:
	•	Default credential abuse
	•	Unauthorized remote access on first boot

Understanding this behavior is critical for:
	•	Secure IoT deployments
	•	Blue-team device hardening
	•	Enterprise headless provisioning pipelines

⸻

Project status

✅ USB RNDIS networking functional
✅ Host-to-device IP communication verified
✅ SSH access established
✅ Headless workflow confirmed

⸻

Next directions
	•	Break this project into reusable modules
	•	Automate host-side validation scripts
	•	Add logging and monitoring for defensive analysis
	•	Expand into wireless attack surface modeling (future repo)

⸻

Ethical use notice

This project is for educational and defensive security learning only, performed on authorized hardware in controlled environments.

