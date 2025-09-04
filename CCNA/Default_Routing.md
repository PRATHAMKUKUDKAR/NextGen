# Default Routing Summary

- **Definition**: A route that is used when no other specific route to a destination is found in the routing table.  
- **Configuration**: Uses the `0.0.0.0 0.0.0.0` destination network (catch-all route).  
- **Purpose**: Acts as a **gateway of last resort**.  
- **Administrative Distance (AD)**: By default `1` (if configured as static).    
- **Security**: ✅ Secure – only routes defined by admin are followed.  
- **Bandwidth Usage**: ✅ Zero – no updates exchanged.  
- **Reliability**: ✅ Works as long as the next-hop is available.  

## Use Cases
- Internet connection from LAN (all traffic goes to ISP router).  
- Stub networks (networks with only one exit point).  
- As a backup when no other route matches.  

---

# Configuration

## Stap 1 : Topology Setup
- Open cisco packate 
- Drag 2 Router
- Drag 2 switch
- Drag 2 pc 
- route to router conect cros cable 
- router,switch, and pc conect stragth cable 

<img width="558" alt="Screenshot 2025-09-04 131424" src="https://github.com/user-attachments/assets/2dce1c16-0954-4a2d-acb1-3589f2162352" />


## Stap 2: Coniguration Router0 (Left) 
```
Router> enable
Router# configure terminal

**LAN side**
Router(config)# interface fastethernet 0/1
Router(config-if)# ip address 10.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="612"  alt="Screenshot 2025-09-04 131810" src="https://github.com/user-attachments/assets/acee1662-79b8-40be-8fdd-c1fba278a2f6" />


```
**Link to Router1**
Router(config)# interface fastethernet 0/0
Router(config-if)# ip address 11.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="630" alt="Screenshot 2025-09-04 131938" src="https://github.com/user-attachments/assets/ecd3d4e6-7452-4a6d-a806-87939857b6f1" />

## Stap 3: Configuretion Router1 (Right)
```
Router> enable
Router# configure terminal

**LAN side**
Router(config)# interface fastethernet 0/1
Router(config-if)# ip address 20.0.0.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="603" alt="Screenshot 2025-09-04 132820" src="https://github.com/user-attachments/assets/2188dc1d-0610-4505-b815-34e8d7a3f26f" />

```
**Link to Router0**
Router(config)# interface fastethernet 0/0
Router(config-if)# ip address 11.0.0.2 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
<img width="602" alt="Screenshot 2025-09-04 133807" src="https://github.com/user-attachments/assets/e4793651-e92d-4777-bc5f-754b5f4974e7" />

## Stap 4: Default route On Router0
```
Router(config)# ip route 0.0.0.0 0.0.0.0 11.0.0.2
```
<img width="866" height="106" alt="Screenshot 2025-09-04 144745" src="https://github.com/user-attachments/assets/61dbaa94-22d1-405b-a5ff-bbeed12fac83" />

## Stap 5: Default route On Router1
```
Router(config)# ip route 0.0.0.0 0.0.0.0 11.0.0.1
```
<img width="840" height="118" alt="Screenshot 2025-09-04 145006" src="https://github.com/user-attachments/assets/4b78b091-655f-4102-8505-d81d2bbb9994" />


## Stap 6: Verification
```
Router# show ip interface brief
```
<img width="1401" height="312" alt="Screenshot 2025-09-04 145132" src="https://github.com/user-attachments/assets/33bd2189-60ef-4952-9b1c-5d086a39f8d0" />

```
Router# show ip route
```
<img width="1875" height="659" alt="Screenshot 2025-09-04 145345" src="https://github.com/user-attachments/assets/27276cc0-69ec-4d88-a8f8-9fc0d8fe88d6" />

## Step 7: Assign IP to Both PCs

1. Click on the **PC** .  
2. Go to the **Desktop / Dashboard** tab.  
3. Click on **IP Configuration**.  
4. Manually assign the **IP Address** and **Default Gateway** for both PCs.  
---

<img width="440" alt="PC1 IP Configuration" src="https://github.com/user-attachments/assets/f2cf49b7-4dd1-4186-8909-3b9a33dfe59a" />

<img width="434" alt="PC2 IP Configuration" src="https://github.com/user-attachments/assets/a2e280bf-5eba-4ca2-8309-8301b5c72a15" />

1. Click on the **PC** .  
2. Go to the **Desktop / Dashboard** tab.
3. Click on Command Prompt.
4. ping 20.0.0.2
