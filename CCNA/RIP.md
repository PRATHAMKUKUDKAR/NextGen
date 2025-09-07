# Routing Information Protocol (RIP)

## What is RIP?
- RIP (Routing Information Protocol) is a **dynamic routing protocol**.
- It automatically shares routing information between routers.
- Uses **Distance Vector algorithm (Bellman-Ford)**.
- Works at the **Network Layer (Layer 3)** of the OSI model.

## Key Features of RIP
- **Metric:** Hop Count (max 15 hops allowed).
- **Protocol:** Uses UDP port **520**.
- **Versions:**
  - **RIP v1** → Classful (no subnet info, outdated).
  - **RIP v2** → Classless (supports VLSM, CIDR, authentication).
- **Updates:** Sends routing updates every **30 seconds**.
- **Administrative Distance (AD):** 120.
- **Small Networks Only:** Not scalable for large networks (because of 15 hop limit).
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

## Step 5: RIP Routing Configuration On Both Router

### Enable RIP On Router 0
```
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 10.0.0.0
Router(config-router)# network 12.0.0.0
Router(config-router)# exit
```
<img width="633" alt="Screenshot 2025-09-07 195558" src="https://github.com/user-attachments/assets/558a93af-023a-40b1-ad6f-e0aaee63e87f" />

### Enable RIP Router 1
```
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 12.0.0.0
Router(config-router)# network 20.0.0.0
Router(config-router)# exit
```
<img width="674" alt="Screenshot 2025-09-07 195838" src="https://github.com/user-attachments/assets/da44b950-e866-4a53-9338-9d4c64bb0db6" />


## Step 6: Verification

### 1. Verify on Routers (Router0 / Router1)
- Open CLI on Router and run:
```
Router> enable
Router# show ip route
```
<img width="657" alt="Screenshot 2025-09-07 200140" src="https://github.com/user-attachments/assets/05afd6c2-5146-4117-a46f-25d5d6b40b8b" />

### 2. Verify from PC0
- Click on **PC0 → Desktop → Command Prompt** 
```
PC> ping 20.0.0.2
```
<img width="638" alt="Screenshot 2025-09-07 200308" src="https://github.com/user-attachments/assets/92332280-89a6-460d-833e-2209610bca62" />
