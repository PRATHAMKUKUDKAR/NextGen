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

## Stap 4: Save Switch0 config
```
Switch0# write memory
```

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
## Stap 7: Configure trunk on Switch1 (link to Switch0)
```
Switch(config)# interface fastethernet0/4
Switch(config-if)# switchport mode trunk
Switch(config-if)# no shutdown
Switch(config-if)# exit
```
## Stap 8: Save Switch2 config
```
Switch# write memory
```
