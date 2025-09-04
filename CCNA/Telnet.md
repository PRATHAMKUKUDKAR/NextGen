# Telnet in Cisco Devices

## What is Telnet?
- Telnet is a protocol used to **remotely access and manage a router/switch via CLI**.  
- Works at the **Application Layer (Layer 7)** of the OSI model.  
- Uses **TCP port 23** by default.  
- Sends all data (including **username & password**) in **plain text** → ❌ Not secure.  
- Still useful in **labs or small test environments** for basic remote access.  
- In real/production networks → **SSH is recommended** (secure alternative).  
 
## Key Points
- `line vty 0 4` → Allows **5 simultaneous remote sessions**.  
- `line vty 0 15` → Allows **16 simultaneous remote sessions**.  

---
# Configuration
## Step 1: Setup Network Topology
- Open Cisco Packet Tracer.
- Drag 1 Router , 1 Switch And 1 pc into the workspace.
- Connect Using cable:-
    - Router → Fa0/0
    - Switch → Fa0/1 ↔ Fa0/2
    - PC0 → Fa0
<img width="616" alt="Screenshot 2025-09-04 232846" src="https://github.com/user-attachments/assets/4216ce93-471c-42be-b2c4-c4edadfd2c5d" />

## Step 2: Configure Router Interface
- Open Router Cli
```
Router> enable
Router# configure terminal
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="679" alt="Screenshot 2025-09-04 235803" src="https://github.com/user-attachments/assets/b7b68efd-1e0a-49ea-89aa-f90ff5861f24" />

## Step 3: Configure Telnet Access (VTY lines)
```
Router(config)# line vty 0 15
Router(config-line)# password 123
Router(config-line)# login
Router(config-line)# exit
```
<img width="387" alt="Screenshot 2025-09-05 000149" src="https://github.com/user-attachments/assets/c4b87f4b-5a98-401a-9f86-cfcf7baf6a43" />


## Step 4: Set Enable Password on Router
```
Router(config)# enable password pratham
Router(config)# exit
```
<img width="473" alt="Screenshot 2025-09-05 000456" src="https://github.com/user-attachments/assets/5e72fba6-51ee-4e5e-a915-097f71ef0799" />

## Step 5: Assign IP to Both PCs

1. Click on the **PC** .  
2. Go to the **Desktop / Dashboard** tab.  
3. Click on **IP Configuration**.  
4. Manually assign the **IP Address** and **Default Gateway** for PCs.  
<img width="439" alt="Screenshot 2025-09-05 000919" src="https://github.com/user-attachments/assets/10d03224-b1c5-4a21-b70f-803a63ef6c24" />

## Step 5: Test Telnet from PC
- Click On PC → Command Prompt:
```
PC> telnet 10.0.0.1
Password: 123
Router>enable
Password: pratham
```
<img width="487" alt="Screenshot 2025-09-05 002503" src="https://github.com/user-attachments/assets/95ca2293-8d82-48a7-90ca-ae1a2529aa23" />

