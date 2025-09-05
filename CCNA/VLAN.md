# VLAN (Virtual Local Area Network)

- **Definition**: VLAN is a logical division of a switch into multiple smaller networks.  
- **OSI Layer**: Works at **Layer 2 (Data Link Layer)**.  
- **VLAN ID Range**: **1–4094** (12-bit ID).  
- **Default VLAN**: VLAN 1 (all switch ports belong to it by default).  
- **Access Port**: Belongs to **one VLAN** only, connects end devices (PCs, printers).  
- **Trunk Port**: Carries **multiple VLANs** between switches/routers using **802.1Q tagging**.  
- **Communication Rule**:  
  - Same VLAN → ✅ communication allowed.  
  - Different VLANs → ❌ cannot communicate without **router/L3 switch**.  
- **Benefits**: Security, reduced broadcasts, better performance, flexibility, scalability.  

---
# Configuration:

## Stap 1 : Topology Setup
- Open cisco packate 
- Drag 3 switch
- Drag 6 pc 
- Port mapping below
  - Switch0
    - Fa0/1 → PC1 (10.0.0.2) → VLAN 10
    - Fa0/2 → PC2 (20.0.0.2) → VLAN 20
    - Fa0/3 → PC3 (30.0.0.2) → VLAN 30
    - Fa0/4 → Trunk to Switch1
  - Switch1
    - Fa0/1 → PC4 (10.0.0.3) → VLAN 10
    - Fa0/2 → PC5 (20.0.0.3) → VLAN 20
    - Fa0/3 → PC6 (30.0.0.3) → VLAN 30
    - Fa0/4 → Trunk to Switch0
<img width="662" alt="Screenshot 2025-09-05 115952" src="https://github.com/user-attachments/assets/49fcdc38-7d4b-4c43-a9c5-ae7354773ec0" />

## Stap 2: Configure VLANs on Switch0
```
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit
Switch(config)# vlan 30
Switch(config-vlan)# name Admin
Switch(config-vlan)# exit
```
<img width="650" alt="Screenshot 2025-09-05 120537" src="https://github.com/user-attachments/assets/683fc88c-ba7a-4de4-a233-fc8c79cb2ada" />


## stap 3: Assign access ports on Switch0
```
Switch(config)# interface fastethernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface fastethernet0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

Switch(config)# interface fastethernet0/3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
Switch(config-if)# exit
```
<img width="606" alt="Screenshot 2025-09-05 122145" src="https://github.com/user-attachments/assets/e98221ad-f212-4f9d-95b8-6cc238a297bc" />

## Stap 4: Configure trunk on Switch0 (link to Switch1)
```
Switch(config)# interface fastethernet0/4
Switch(config-if)# switchport mode trunk
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
<img width="597" alt="Screenshot 2025-09-06 002757" src="https://github.com/user-attachments/assets/687946d2-e60f-40ee-a915-f2a70b2200ba" />

## Stap 4: Save Switch0 config
```
Switch0# write memory
```
<img width="421" alt="Screenshot 2025-09-06 002900" src="https://github.com/user-attachments/assets/63516611-9490-456b-adfb-b093a5df19d8" />

## Stap 5: Repeat on Switch1 — create VLANs
```
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit
Switch(config)# vlan 30
Switch(config-vlan)# name Admin
Switch(config-vlan)# exit
```
<img width="682" alt="Screenshot 2025-09-06 003720" src="https://github.com/user-attachments/assets/af4af019-e02f-4aa3-a299-9a56345902a5" />


## Stap 6: Assign access ports on Switch1
```
Switch(config)# interface fastethernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface fastethernet0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

Switch(config)# interface fastethernet0/3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
Switch(config-if)# exit
```
<img width="596" alt="Screenshot 2025-09-06 004503" src="https://github.com/user-attachments/assets/dcfb375a-8b34-465c-8b80-92affeb6c5e4" />

## Stap 7: Configure trunk on Switch1 (link to Switch0)
```
Switch(config)# interface fastethernet0/4
Switch(config-if)# switchport mode trunk
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
<img width="572" alt="Screenshot 2025-09-06 004840" src="https://github.com/user-attachments/assets/75143ff6-2d8f-4ca8-9cb3-527d755a841c" />

## Stap 8: Save Switch2 config
```
Switch# write memory
```
<img width="482" alt="Screenshot 2025-09-06 004933" src="https://github.com/user-attachments/assets/51db9bcf-0bb6-4b34-89e1-8f0a7a409dd0" />

## Stap 9: Verification
### Check VLANs
```
Switch# show vlan brief
```
<img width="690" alt="Screenshot 2025-09-06 010556" src="https://github.com/user-attachments/assets/974f7f95-7c11-4755-abb5-878b0491609a" />

### Ping Vlan 10 Pc to vlan 10 
```
PC>ping 10.0.0.3
```
<img width="591" alt="Screenshot 2025-09-06 010918" src="https://github.com/user-attachments/assets/3b1e3b72-6ac2-4541-a58e-72c5b64fe5ad" />

### Ping vlan 10 to vlan 20 
```
PC>ping 20.0.0.3
```
<img width="545" alt="Screenshot 2025-09-06 011207" src="https://github.com/user-attachments/assets/3456fb2b-95bb-4794-a972-fa66ff0ca1e2" />

**not working**
