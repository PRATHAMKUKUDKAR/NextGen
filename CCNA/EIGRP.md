# Enhanced Interior Gateway Routing Protocol (EIGRP)

## What is EIGRP?
- EIGRP is a **dynamic routing protocol**.
- Originally **Cisco-proprietary**, but now an **open standard**.
- It is a **Hybrid Protocol** (combines Distance Vector + Link State concepts).
- Designed for **medium and large networks**.

---

## Key Features
- **Metric:** Composite (uses **Bandwidth + Delay**).
- **Protocol Number:** 88 (uses IP packets directly, not TCP/UDP).
- **Administrative Distance (AD):**
  - **90** → Internal EIGRP  
  - **170** → External EIGRP  
- **Supports:**
  - VLSM (Variable Length Subnet Mask)  
  - CIDR (Classless Inter-Domain Routing)  
  - Authentication  
- **Updates:** Sends **partial updates** (not the entire table like RIP).
- **Convergence:** Very fast (uses DUAL algorithm).

---

## Algorithm Used
- **DUAL (Diffusing Update Algorithm):**
  - Finds the **best path (Successor)**.
  - Maintains a **backup path (Feasible Successor)**.
  - Ensures **loop-free routing**.

---

# Configuration
## Step 1: Network Topology

### Devices Required
- 2 Routers 
- 2 Switches
- 2 PCs

### Connections
1. **Router0 Fa0/0 ↔ Router1 Fa0/0** (Cross Cable)  
2. **Router0 Fa0/1 ↔ Switch0 Fa0/1** (Straight Cable)  
3. **Router1 Fa0/1 ↔ Switch1 Fa0/1** (Straight Cable)  
4. **PC0 FastEthernet0 ↔ Switch0 Fa0/2** (Straight Cable)  
5. **PC1 FastEthernet0 ↔ Switch1 Fa0/2** (Straight Cable)  


### IP Addressing Plan
- **PC0** → `10.0.0.2 `, Gateway: `10.0.0.1`  
- **Router0 Fa0/1** → `10.0.0.1 `  
- **Router0 Fa0/0** → `12.0.0.1 `  
- **Router1 Fa0/0** → `12.0.0.2 `  
- **Router1 Fa0/1** → `20.0.0.1 `  
- **PC1** → `20.0.0.2 `, Gateway: `20.0.0.1`  

<img width="600" alt="Screenshot 2025-09-07 191404" src="https://github.com/user-attachments/assets/2117845e-24d2-4748-bb91-f1d7e4fee5cc" />

## Step 2: Router 0 Configuration

### Assign IPs to interfaces
```
Router> enable
Router# configure terminal

Router(config)# interface fa0/0
Router(config-if)# ip address 12.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface fa0/1
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="687" alt="Screenshot 2025-09-07 191857" src="https://github.com/user-attachments/assets/b2a4455f-706a-4c8b-8c83-7791741d4a10" />


## Step 3: Router 1 Configuration

### Assign IPs to interfaces
```
Router> enable
Router# configure terminal

Router(config)# interface fa0/0
Router(config-if)# ip address 12.0.0.2 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface fa0/1
Router(config-if)# ip address 20.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="646" alt="Screenshot 2025-09-07 192447" src="https://github.com/user-attachments/assets/a5885d79-dfac-4a86-be1f-f76ee0ee69a0" />

## Step 4: Configure PCs

### PC 0
  - Click on **PC0 → Desktop → IP Configuration** 
  - IP Address: 10.0.0.2
  - Subnet Mask: 255.0.0.0
  - Default Gateway: 10.0.0.1
<img width="436" alt="Screenshot 2025-09-07 192641" src="https://github.com/user-attachments/assets/15645237-d8ef-4fd0-a960-1345c9467629" />

### PC1
  - Click on **PC1 → Desktop → IP Configuration** 
  - IP Address: 20.0.0.2
  - Subnet Mask: 255.0.0.0
  - Default Gateway: 20.0.0.1
<img width="436" alt="Screenshot 2025-09-07 192751" src="https://github.com/user-attachments/assets/6512cc70-3094-47a9-9482-8f9e884b1545" />

## Step 5: EIGRP Routing Configuration On Both Router

### Enable EIGRP On Router 0
```
Router(config)# router eigrp 100
Router(config-router)# network 10.0.0.0 0.0.0.255
Router(config-router)# network 12.0.0.0 0.0.0.255
Router(config-router)# exit
```
<img width="634" alt="Screenshot 2025-09-07 231237" src="https://github.com/user-attachments/assets/e8613980-99f0-4c89-b5a1-465d7c8b6861" />


### Enable EIGRP On Router 1
```
Router(config)# router eigrp 100
Router(config-router)# network 12.0.0.0 0.0.0.255
Router(config-router)# network 20.0.0.0 0.0.0.255
Router(config-router)# exit
```
<img width="613" alt="Screenshot 2025-09-07 231452" src="https://github.com/user-attachments/assets/dc09fd42-c706-4b05-a8c2-c3cc1d50d90f" />


## Step 6: Verification

### 1. Verify on Routers (Router0 / Router1)
- Open CLI on Router and run:
```
Router> enable
Router# show ip route
```
<img width="606" alt="Screenshot 2025-09-07 233059" src="https://github.com/user-attachments/assets/a500785b-f148-45f4-a57b-c26f5f204221" />


### 2. Verify from PC0
- Click on **PC0 → Desktop → Command Prompt** 
```
PC> ping 20.0.0.2
```
<img width="664" alt="Screenshot 2025-09-07 232059" src="https://github.com/user-attachments/assets/7742dc19-9987-43d7-bb3d-8133afc676f8" />
