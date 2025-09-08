# OSPF (Open Shortest Path First)

## What is OSPF?
- A **dynamic routing protocol** used in routers.
- Helps routers **automatically learn paths** to other networks.
- Uses **Shortest Path First (Dijkstra Algorithm)** to find the best route.
- Works at **Layer 3 (Network Layer)**.

---

## Key Points
- **Metric:** Cost (decides best path → lower cost = better).
- **Protocol Number:** 89 (special number for OSPF).
- **Fast:** Detects changes quickly (faster than RIP).
- **Supports:** VLSM, CIDR, Authentication.
- **Area Concept:** 
  - **Area 0 = Backbone (main highway)**
  - Other areas (1, 2, …) = side roads connected to backbone.
- **Administrative Distance (AD):** 110 (trust level).

---

## OSPF Packet Types (Simple)
1. **Hello** → "Hi, I’m here!" (to find neighbors).
2. **DBD** → "Here’s my map summary."
3. **LSR** → "I need more details."
4. **LSU** → "Here’s the full map."
5. **LSAck** → "Got it, thanks!"

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

### Enable OSPF On Router 0
```
Router(config)# router ospf 1
Router(config-router)# network 10.0.0.0 0.0.0.255 area 2
Router(config-router)# network 12.0.0.0 0.0.0.255 area 2
Router(config-router)# exit
```
<img width="654" alt="Screenshot 2025-09-08 102833" src="https://github.com/user-attachments/assets/6d398723-d320-4810-9ced-a4e372cfcfe4" />

### Enable OSPF Router 1
```
Router(config)# router ospf 1
Router(config-router)# network 12.0.0.0 0.0.0.255 area 2
Router(config-router)# network 20.0.0.0 0.0.0.255 area 2
Router(config-router)# exit
```
<img width="615" alt="Screenshot 2025-09-08 103112" src="https://github.com/user-attachments/assets/dc39084e-5d62-45c2-b6b4-a3563355abef" />


## Step 6: Verification

### 1. Verify on Routers (Router0 / Router1)
- Open CLI on Router and run:
```
Router> enable
Router# show ip route
```
<img width="647" alt="Screenshot 2025-09-08 103443" src="https://github.com/user-attachments/assets/f9760b64-7297-4d9f-9eca-3af3830ec550" />

### 2. Verify from PC0
- Click on **PC0 → Desktop → Command Prompt** 
```
PC> ping 20.0.0.2
```
<img width="642" alt="Screenshot 2025-09-08 103611" src="https://github.com/user-attachments/assets/89f6c987-3ba1-4e6d-b383-2725550b44e0" />
