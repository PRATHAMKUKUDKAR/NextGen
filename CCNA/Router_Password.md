# Router Password Summary  

## What is a Password?  
- Used to protect router/switch from unauthorized access.  

## Why is it Important?  
- Secures the device configuration.  
- Prevents unauthorized users from making changes.  

## Types of Passwords  

### Enable Password  
- Stored in **plain text**.  
- **Less secure**.  

### Enable Secret  
- Stored in **encrypted form (MD5)**.  
- **More secure**.  
- Overrides enable password if both are set.  

# Configuration
## Network Topology
- Open Cisco Packet Tracer.
- Drag and drop a Router into the workspace.
- Click on the router → go to CLI tab.
## Step 1: Configuration Modes
```bash
Router> enable
Router# configure terminal
```
<img width="635" height="435" alt="Screenshot 2025-09-01 231458" src="https://github.com/user-attachments/assets/54742d0a-18b6-43de-b781-a4744b7f7d0a" />

## step 2: Set enable password (plain text)
```bash
Router(config)# enable password cisco123
```
<img width="417" height="160" alt="Screenshot 2025-09-01 231946" src="https://github.com/user-attachments/assets/d710ed7e-2c81-4e00-83e5-da72a201e8cf" />

## step 3: Set enable secret (encrypted)
```bash
Router(config)# enable secret admin123
```
<img width="378" height="213" alt="Screenshot 2025-09-01 232058" src="https://github.com/user-attachments/assets/d7c0e291-c2e1-4317-a664-2af2faed0766" />

## step 4: Save configuration
```bash
Router(config)# exit
Router# copy running-config startup-config
```
<img width="428" height="190" alt="Screenshot 2025-09-01 232334" src="https://github.com/user-attachments/assets/5b2c59ac-0b53-439c-b852-4f436a0d82ea" />

## step 5: Check that passwords are configured
```bash
Router# show running-config
```
<img width="473" height="545" alt="Screenshot 2025-09-01 232625" src="https://github.com/user-attachments/assets/229c7ed1-2200-4d94-9edb-6078936f38e0" />

# Verification
## step 1: Exit session
```bash
Router# exit
```
## step 2: Reconnect & test
```bash
Router> enable
Password: (enter admin123)
Router#
```
<img width="481" height="530" alt="Screenshot 2025-09-01 232917" src="https://github.com/user-attachments/assets/f7b47e24-dea8-4a0f-a0c0-4a98c65deee3" />

---

- If you type cisco123, it will not work because enable secret overrides it.
- admin123 will allow access.
