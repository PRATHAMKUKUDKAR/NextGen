# Backup Router Using TFTP Server

## Purpose of Backup
- To save the router’s configuration file externally so it can be restored in case of failure, corruption, or migration.
- Ensures network continuity and avoids reconfiguring from scratch.

## TFTP (Trivial File Transfer Protocol)
- A simple protocol to transfer files over a network.
- Lightweight, does not require authentication, and works best in trusted LAN environments.
- Commonly used for router/switch configuration backups.



## Step-by-Step Configuration 

### Step 1: Setup Network Topology
- Open Cisco Packet Tracer.
- Drag 1 Router and 1 Server into the workspace.
- Connect Router FastEthernet0/0 → Server FastEthernet using Cross Cable.
<img width="480" height="270" alt="Screenshot 2025-09-02 011554" src="https://github.com/user-attachments/assets/02332ad8-2e04-420e-9d4b-9e1d1858cb97" />

### Step 2: Turn ON TFTP Service on Server
- Click Server → Config → TFTP.
- Ensure TFTP is ON.
<img width="439" height="339" alt="Screenshot 2025-09-02 012128" src="https://github.com/user-attachments/assets/517adb11-393d-4edb-94c1-adb621db47ce" />

### Step 3: Configure IP on Server
- Go to Desktop → IP Configuration.
- Set:
  - IP Address: 10.0.0.2
  - Subnet Mask: 255.0.0.0
<img width="433" height="318" alt="Screenshot 2025-09-02 095334" src="https://github.com/user-attachments/assets/209c77fc-e840-4e78-b2e0-e73c242059d5" />

### Step 4: Configure Router Modes
- Click on the router → go to **CLI tab**.
```bash
Router> enable
Router# configure terminal
```
<img width="509" height="402" alt="Screenshot 2025-09-02 095536" src="https://github.com/user-attachments/assets/d7eb17c4-4171-4933-a76a-cc251a2bdedd" />

### Step 5: Assign IP Address on Router
```bash
Router(config)# interface fastEthernet0/0
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
```
<img width="483" height="317" alt="Screenshot 2025-09-02 095734" src="https://github.com/user-attachments/assets/3aceff1a-0522-43d3-ba93-8a07fdaa6200" />

### step 6: Exit Configuration Mode and Save
```bash
Router(config-if)# exit
Router(config)# exit
Router# copy running-config startup-config
```
<img width="553" height="231" alt="Screenshot 2025-09-02 095925" src="https://github.com/user-attachments/assets/4cd0b6b1-6c13-4323-adfa-b32d07928af0" />

### Step 7: Verify Connectivity

- Check interface:
```bash
Router# show ip interface brief
```
<img width="576" height="447" alt="Screenshot 2025-09-02 100030" src="https://github.com/user-attachments/assets/fdea0419-bbec-4e5b-b0da-ac00a8689d78" />

- Test communication:
```bash
SERVER>ping 10.0.0.1
```
<img width="584" height="471" alt="Screenshot 2025-09-02 100244" src="https://github.com/user-attachments/assets/14f29fa5-3101-4586-b1e1-4cd917c8ca29" />

### Step 8: Backup Router Config to TFTP Server
```bash
Router# copy startup-config tftp
```
- Enter prompts:
    - Remote host: 10.0.0.2
    - Filename: abc
<img width="592" height="336" alt="Screenshot 2025-09-02 100523" src="https://github.com/user-attachments/assets/bd502c16-2482-42cd-934f-0428381dc816" />

- Verify backup on Server → Services → TFTP.

<img width="723" height="456" alt="Screenshot 2025-09-02 101247" src="https://github.com/user-attachments/assets/ed3b4d48-3a53-4a4c-aa73-3fae596e841c" />
