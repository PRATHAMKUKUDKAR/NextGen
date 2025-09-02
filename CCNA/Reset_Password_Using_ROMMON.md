# Cisco Router Password Recovery Using ROMMON
---

## Purpose
- Routers are core network devices that control traffic and settings.
- Passwords protect router access and prevent unauthorized configuration changes.
- Proper password use reduces risk of downtime, misconfiguration, and security breaches.


## Password Recovery (Conceptual Overview)
- Mistakes and forgotten passwords happen — recovery is necessary.
- Cisco routers have a low-level recovery mode (ROMMON) that allows administrators to temporarily bypass the saved configuration.
- The recovery process **does not** destroy the configuration by default: it temporarily ignores it, allowing an admin to set a new secret and then restore normal boot behavior.
- This approach prevents full reconfiguration while enabling secure restoration of access.

## Config-Register Values (What They Mean)
- `0x2142` — Instructs the router to ignore the startup configuration during boot (used for password recovery).
- `0x2102` — Normal boot behavior: load startup-config from NVRAM (typical default for production devices).

# Configuration
## Step 1: Network Topology
- Open Cisco Packet Tracer.
- Drag and drop a Router into the workspace.
- Click on the router → go to CLI tab.

<img width="805" height="425" alt="Screenshot 2025-09-02 114604" src="https://github.com/user-attachments/assets/a2e0e796-5583-46f9-b501-1b32f8829f70" />

## Step 2: Configuration Modes
```bash
Router> enable
Router# configure terminal
```
<img width="646" height="295" alt="Screenshot 2025-09-02 114904" src="https://github.com/user-attachments/assets/0f048b1c-9a0e-4523-bf7d-324d337e46b8" />

## Step 3: Set Password And Save Configuration
```bash
Router(config)# enable secret pratham123
Router# copy running-config startup-config
```

<img width="646" height="460" alt="Screenshot 2025-09-02 115345" src="https://github.com/user-attachments/assets/5cfcabc1-a91d-434b-aaaa-bc3e7ad69dfc" />

## Step 4: Reload & Test
```bash
Router# reload
```
<img width="622" height="402" alt="Screenshot 2025-09-02 115908" src="https://github.com/user-attachments/assets/7b80773d-d094-4318-b937-c2b726ece3bd" />

- **After reload:**
```
Router> enable
Password: pratham123
Router# 
```
- Password is now active & secured.

## Step 5: Enter ROMMON Mode
- Power OFF → ON router.

<img width="623" height="418" alt="Screenshot 2025-09-02 121531" src="https://github.com/user-attachments/assets/3a3d1622-9688-4edf-a347-3e5771280252" />


- **Press Ctrl+6+c during boot.**
- **You’ll see:**
```
rommon 1 >
```
<img width="648" height="334" alt="Screenshot 2025-09-02 121248" src="https://github.com/user-attachments/assets/66c08760-8c07-41b4-a2e0-5f84209a51e6" />

## step 6: Ignore Startup Configuration (Bypass Password) And Reset Router
```
rommon 1 > confreg 0x2142
rommon 2 > reset
```
<img width="682" height="403" alt="Screenshot 2025-09-02 122346" src="https://github.com/user-attachments/assets/b03b1d98-779c-4a3d-9dbe-a711549a6940" />


## Step 7: Enter Enable Mode (No Password Needed) And Restore Old Config Into RAM
```
Router> enable
Router#
Router# copy startup-config running-config
```
<img width="599" height="434" alt="Screenshot 2025-09-02 122742" src="https://github.com/user-attachments/assets/774ca351-7a50-4a5f-b8ee-cf4adcf43e3b" />

## Step 8: Set New Password
```
Router# configure terminal
Router(config)# enable secret newpass123
Router(config)# exit
```
<img width="667" height="442" alt="Image" src="https://github.com/user-attachments/assets/671c4149-82f1-47c5-946b-eb2dd533d48b" />

## Step 9: Restore Default Boot Behavior
```
Router(config)# config-register 0x2102
Router# copy running-config startup-config
Router# reload
```
<img width="518" height="467" alt="Image" src="https://github.com/user-attachments/assets/30668275-bd18-43d2-a810-2048f5d45451" />

