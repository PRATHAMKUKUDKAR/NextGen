
# Step 1: Network Topology

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



# Configuration

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

## Step 4: Configure PCs

### PC 0
  - IP Address: 10.0.0.2
  - Subnet Mask: 255.0.0.0
  - Default Gateway: 10.0.0.1

### PC1
  - IP Address: 20.0.0.2
  - Subnet Mask: 255.0.0.0
  - Default Gateway: 20.0.0.1

## Step 5: RIP Routing Configuration On Both Router

### Enable RIP On Router 0
```
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 10.0.0.0
Router(config-router)# network 12.0.0.0
Router(config-router)# exit
```
### Enable RIP Router 1
```
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 12.0.0.0
Router(config-router)# network 20.0.0.0
Router(config-router)# exit
```
## Step 6: Verification

### 1. Verify on Routers (Router0 / Router1)
- Open CLI on Router and run:
```
Router> enable
Router# show ip route
```
### 2. Verify from PC0
- Click on **PC0 → Desktop → Command Prompt** 
```
PC> ping 20.0.0.2
```
