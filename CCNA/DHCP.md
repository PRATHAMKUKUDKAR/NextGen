
## What is DHCP?
- **DHCP (Dynamic Host Configuration Protocol)** is used to **automatically assign IP addresses** and other network parameters to devices.
- Cisco devices (routers/switches) can act as:
  - **DHCP Server** → Assigns IP addresses.
  - **DHCP Relay Agent** → Forwards client requests to a remote DHCP server.
- Works using the **DORA process**:
  1. Discover  
  2. Offer  
  3. Request  
  4. Acknowledge  

---

## DHCP Configuration on Cisco Router

### Step 1: Network Topology
- **1 Router**
- **1 PC**
- **1 Cross Cable**

**Connection:**
- Router **FastEthernet0/0** ↔ PC **FastEthernet0**
<img width="548" height="285" alt="Screenshot 2025-09-03 204658" src="https://github.com/user-attachments/assets/e9fb495b-7c7d-4e59-bebb-e1c9eb0bc047" />

---

### Step 2: Enter privileged & configuration mode (CLI)
- Click on the router → go to **CLI tab**.
```bash
Router> enable
Router# configure terminal
```
<img width="506" height="401" alt="Screenshot 2025-09-03 204904" src="https://github.com/user-attachments/assets/e29da761-fb66-42c1-8537-9a3bae35584b" />

### 3️: Configure IP on router interface
```
Router(config)# interface fastethernet0/0
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="508" height="487" alt="Screenshot 2025-09-03 205131" src="https://github.com/user-attachments/assets/87894316-22da-4a7d-a4ff-ae6ad10380a7" />

### Step 4: Create DHCP pool
```
Router(config)# ip dhcp pool pratham
Router(dhcp-config)# network 10.0.0.0 255.0.0.0
Router(dhcp-config)# default-router 10.0.0.1
Router(dhcp-config)# exit
```
<img width="551" height="349" alt="Screenshot 2025-09-03 205340" src="https://github.com/user-attachments/assets/ae496adf-ef47-4a57-a0b2-4dd4570acbf5" />

### Step 5️: Save configuration
```
Router# copy running-config startup-config
```
### Step 6: PC Configuration
- Go to Desktop → IP Configuration.
- Select DHCP.
- The PC will automatically get:
    - IP Address: 10.0.0.2 (from DHCP pool)
    - Subnet Mask: 255.0.0.0
    - Default Gateway: 10.0.0.1
<img width="536" height="521" alt="Screenshot 2025-09-03 205506" src="https://github.com/user-attachments/assets/8bf739fd-9e75-4eca-a0d3-d62205025e7a" />


