# Basic Configuration (1 Router + 1 PC)

## 🖧 Topology

### 🔹 Step 1: Devices Required
- 1 Router  
- 1 PC  
- 1 Copper Straight-Through Cable  

---

### Step 2: Connections
- Connect **PC0 → FastEthernet0**  
- Connect **Router0 → FastEthernet0/0**  

<img width="375" alt="Screenshot 2025-09-12 214649" src="https://github.com/user-attachments/assets/a300017c-04c6-4353-b90f-ee46fa8e7611" />

---

### Step 3: Router Configuration
1. Click on router
2. Go to cli

   <img width="550" alt="Screenshot 2025-09-12 215128" src="https://github.com/user-attachments/assets/8dd55ba7-ea31-4dfc-ba4c-309973584154" />

3. Enter Privileged Mode
```
Router> enable
```
<img width="652" alt="Screenshot 2025-09-12 215229" src="https://github.com/user-attachments/assets/08503f29-77a7-4cfa-9463-b230f22bf908" />

4. Enter Global Configuration Mode
```
Router# configure terminal
```
<img width="513" alt="Screenshot 2025-09-12 215321" src="https://github.com/user-attachments/assets/cb1b9671-703b-41ab-b349-db12390a42e7" />


5. Set Hostname
```
Router(config)# hostname R1
pratham(config)#
```
<img width="530" alt="Screenshot 2025-09-12 215431" src="https://github.com/user-attachments/assets/44ab3fc8-b54e-4a73-ad12-0cf665a35cc6" />


6. Set Enable Password (for privileged exec mode)
```
Pratham(config)# enable password Praju
```
<img width="503" alt="Screenshot 2025-09-12 215604" src="https://github.com/user-attachments/assets/5ce0acaa-7e22-4a73-8052-589f80d543a8" />


7. Encrypt All Passwords
```
Pratham(config)# service password-encryption
```
<img width="500" alt="Screenshot 2025-09-12 215758" src="https://github.com/user-attachments/assets/45c7df38-3bc8-4f20-b74a-8eae9fead411" />


8. Set MOTD Banner (Message of the Day)
```
Pratham(config)# banner motd # Welcome To NextGen Education #
```
<img width="553" alt="Screenshot 2025-09-12 215958" src="https://github.com/user-attachments/assets/ca1e55dd-d930-489c-bf14-a947fd5776b9" />



9. Configure Interfaces
```
Pratham(config)# interface fastEthernet 0/0
Pratham(config-if)# ip address 192.168.1.1 255.255.255.0
Pratham(config-if)# no shutdown
Pratham(config-if)# exit
```
<img width="557" alt="Screenshot 2025-09-12 220132" src="https://github.com/user-attachments/assets/78524d8d-2c07-4dd9-9340-0fff5d4df3bf" />

 10. Save Configuration
```
Pratham# copy running-config startup-config
```
<img width="908" height="280" alt="Screenshot 2025-09-12 220324" src="https://github.com/user-attachments/assets/58174e4b-eb4e-40b0-a4c3-280408f7e7c5" />

11. Pc Configuration
- Click PC0 → Desktop → IP Configuration.

<img width="527" height="430" alt="image" src="https://github.com/user-attachments/assets/fba01614-370d-465c-96fc-e6e31b259c5e" />

- Enter:
  - IP Address: 10.0.0.2
  - Subnet Mask: 255.0.0.0
  - Default Gateway: 10.0.0.1
  <img width="538" alt="Screenshot 2025-09-12 221129" src="https://github.com/user-attachments/assets/ae230d21-b30a-4a60-83ff-93095160d007" />

  
 ### Verification Commands

1. Check hostname & banner
```
Pratham# show running-config
```
<img width="566" alt="Screenshot 2025-09-12 220459" src="https://github.com/user-attachments/assets/7ed216a3-cc04-4e10-9bd1-a57b1d29cd61" />


2. Check interfaces
```
Pratham# show ip interface brief
```
<img width="542" alt="image" src="https://github.com/user-attachments/assets/ff5f8177-f930-4c86-a120-5693240f1a74" />


3. Test connectivity
```
Pratham# ping 192.168.1.2
```
<img width="542" alt="Screenshot 2025-09-12 221219" src="https://github.com/user-attachments/assets/d5b900ef-275f-435c-bada-d6864e19841d" />
