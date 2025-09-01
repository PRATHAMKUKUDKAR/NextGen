# Basic LAN Connectivity using Switch in Cisco Packet Tracer

This guide explains how to establish LAN connectivity between two PCs using a switch in Cisco Packet Tracer.

---

## Step 1: Setup Network Topology
1. Open **Cisco Packet Tracer**.  
2. Drag and drop:  
   - **2 PCs (PC0 & PC1)**  
   - **1 Switch (2960/2950)**  
3. Connect devices using **Copper Straight-Through Cables** (modern switches auto-detect, so cross cable is not required):  
   - **PC0 → Switch (Fa0/1)**  
   - **PC1 → Switch (Fa0/2)**  

---

## Step 2: Assign IP Addresses to PCs
Go to each PC → **Desktop → IP Configuration**  

- **PC0**  
  - IP Address: `10.0.0.1`  
  - Subnet Mask: `255.0.0.0`  

- **PC1**  
  - IP Address: `10.0.0.2`  
  - Subnet Mask: `255.0.0.0`  

✅ Both PCs are now in the **same network**.  

---

## Step 3: Switch CLI Configuration (Basic Setup)

Open the **Switch CLI** and enter:

```bash
Switch> enable
Switch# configure terminal
