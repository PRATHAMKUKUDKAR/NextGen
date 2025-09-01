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

### Step 2: Turn ON TFTP Service on Server
- Click Server → Services → TFTP.
- Ensure TFTP is ON.

### Step 3: Configure IP on Server
- Go to Desktop → IP Configuration.
- Set:
  - IP Address: 10.0.0.2
  - Subnet Mask: 255.0.0.0

### Step 4: Configure Router Modes
```bash
Router> enable
Router# configure terminal
```
### Step 5: Assign IP Address on Router
```bash
Router(config)# interface fastEthernet0/0
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
```
### step 6: Exit Configuration Mode and Save
```bash
Router(config-if)# exit
Router(config)# exit
Router# copy running-config startup-config
```
### Step 7: Verify Connectivity

- Check interface:
```bash
Router# show ip interface brief
```
- Test communication:
```bash
Router# ping 10.0.0.2
```
### Step 8: Backup Router Config to TFTP Server
```bash
Router# copy startup-config tftp
```

- Enter prompts:

    - Remote host: 10.0.0.2
    - Filename: abc

-Verify backup on Server → Services → TFTP.
