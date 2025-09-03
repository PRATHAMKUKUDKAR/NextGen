# SWITCHES CONNECTED TO END DEVICES

## Switch Basics Notes 

- **Switch** is a networking device used to connect multiple devices (PCs, printers, servers) in a **LAN**.  
- Operates at **Layer 2 (Data Link Layer)** of the OSI model.  
- Uses **MAC addresses** to forward data to the correct device.  
- Each port is a **separate collision domain**, reducing data collisions.  
- Faster and more efficient than hubs because it sends data only to the **intended device**.  
  
This guide explains how to establish LAN connectivity between two PCs using a switch in Cisco Packet Tracer.
---

## Step 1: Setup Network Topology
1. Open **Cisco Packet Tracer**.  
2. Drag and drop:  
   - **2 PCs (PC0 & PC1)**  
   - **1 Switch**  
3. Connect devices using **Copper Straight-Through Cables** (modern switches auto-detect, so cross cable is not required):  
   - **PC0 → Switch (Fa0/1)**  
   - **PC1 → Switch (Fa0/2)**  
<img width="404" height="333" alt="Screenshot 2025-09-01 201520" src="https://github.com/user-attachments/assets/b264e6c2-f3e3-42ca-ac89-70d4e990a187" />

---

## Step 2: Assign IP Addresses to PCs
Go to each PC → **Desktop → IP Configuration**  

- **PC0**  
  - IP Address: `10.0.0.1`  
  - Subnet Mask: `255.0.0.0`  
<img width="433" height="319" alt="Screenshot 2025-09-01 201724" src="https://github.com/user-attachments/assets/eb0c8e69-704a-4c30-942f-bbbda7209ee4" />

- **PC1**  
  - IP Address: `10.0.0.2`  
  - Subnet Mask: `255.0.0.0`  
<img width="430" height="326" alt="Screenshot 2025-09-01 201815" src="https://github.com/user-attachments/assets/969b8ea6-8eda-4ab7-aded-27f22ef58b27" />

✅ Both PCs are now in the **same network**.  

---

## Step 3: Switch CLI Configuration (Basic Setup)

Open the **Switch CLI** and enter:

```bash
Switch> enable
Switch# configure terminal
```
<img width="560" height="262" alt="Screenshot 2025-09-01 202039" src="https://github.com/user-attachments/assets/7ad53db1-8826-4e17-a658-f65a432f4cb1" />

## Step 4: Enable Interfaces in Switch CLI

```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
<img width="530" height="109" alt="Screenshot 2025-09-01 202145" src="https://github.com/user-attachments/assets/4da46432-ab5f-40c0-ae06-8eb59ad629b6" />


```bash
Switch(config)# interface fastEthernet 0/2
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
<img width="504" height="174" alt="Screenshot 2025-09-01 202236" src="https://github.com/user-attachments/assets/14c4bdb3-eef9-4966-aadd-b89cff1552dd" />

## Stap 5: Save Configuration
<img width="368" height="131" alt="Screenshot 2025-09-01 202440" src="https://github.com/user-attachments/assets/900c9496-2e33-4e92-9fbf-390e96e712bb" />


## Step 6: Verification
On PC0 Command Prompt:
 - ping 10.0.0.2
 - If successful, connectivity is established.

<img width="561" height="418" alt="Screenshot 2025-09-01 202543" src="https://github.com/user-attachments/assets/df3b0d30-843e-41fb-bdc2-7fe89c6a73f9" />
