# Static Routing Summary 

- **Definition**: A routing method where routes are manually configured by the network administrator.  
- **Configuration**: Admin specifies **destination network + subnet mask + next-hop IP address or exit interface**.  
- **No Updates**: Static routes do not send or receive routing updates.  
- **Administrative Distance (AD)**: Always `1` (very reliable and preferred over dynamic protocols if both exist).  
- **Security**: ✅ Very secure – no external routing updates can influence it.  
- **Bandwidth Usage**: ✅ Zero – no periodic updates are exchanged.  
- **Reliability**: ✅ High – works as long as administrator sets correct routes.  

- **Use Cases**:  
  - Small networks  
  - Networks with fixed topology  
  - Backup routes (Floating Static Routes with higher AD)  
  - Stub networks (single path to exit)  

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

## Stap 4: Static route On Router0
```
Router(config)# ip route 20.0.0.0 255.0.0.0 11.0.0.2
```
<img width="623" alt="Screenshot 2025-09-04 133900" src="https://github.com/user-attachments/assets/a86db977-8eb2-4266-85af-a5e6d5828d41" />

## Stap 5: Static route On Router1
```
Router(config)# ip route 10.0.0.0 255.0.0.0 11.0.0.1
```
<img width="607" alt="Screenshot 2025-09-04 133946" src="https://github.com/user-attachments/assets/656207bc-8734-445a-86a2-eb5bcf81b950" />

## Stap 6: Verification
```
Router# show ip interface brief
```
<img width="624" alt="Screenshot 2025-09-04 134207" src="https://github.com/user-attachments/assets/b5f6b0d0-e643-467e-90d3-e6419d71e0fb" />

```
Router# show ip route
```
<img width="1391" height="474" alt="Screenshot 2025-09-04 134255" src="https://github.com/user-attachments/assets/dc69dae5-a77f-43e9-a9c2-29e5a02dc301" />

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
<img width="646" alt="Screenshot 2025-09-04 140936" src="https://github.com/user-attachments/assets/a3b09ce8-d596-4d7c-90d3-dc9ae449b486" />
