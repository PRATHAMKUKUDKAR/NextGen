# 🖥️ MCSA Practical Lab – Windows 10 (Client) + Windows Server 2016 (Server1 & Server2)

This lab demonstrates how to set up **1 Windows 10 Client** and **2 Windows Server 2016 machines** in **VMware Workstation**, configure networking, assign IPs, disable firewalls, and test connectivity.

---

## 🔹 Step 1: Open VMware
- Launch **VMware Workstation / VMware Player**.
- Click **Create a New Virtual Machine**.

---

## 🔹 Step 2: Install Windows 10 (Client)
- Select **ISO image** → Windows 10 ISO.
- Install Windows 10 normally.

---

## 🔹 Step 3: Install Windows Server 2016 (Server1)
- Create a new VM → use **Windows Server 2016 ISO**.
- Complete installation.

---

## 🔹 Step 4: Install Windows Server 2016 (Server2)
- Create a new VM → use **Windows Server 2016 ISO**.
- Complete installation.

---

## 🔹 Step 5: Rename Devices (VM Names)

### 🖥️ Rename Client (Windows 10)
1. **Windows Icon → Settings → System**  
   ![Settings](https://github.com/user-attachments/assets/b1474db2-85e1-4e6a-8a85-134fd09a6bce)  
   ![System](https://github.com/user-attachments/assets/eb174fc2-b344-4114-806d-fc58edb4bacd)

2. Scroll down → **About → Advanced System Settings**  
   ![About](https://github.com/user-attachments/assets/354a0d8e-156e-408a-976c-bab76977b7cb)

3. Open **Computer Name** tab → Rename PC → `Client`.

---

### 🖥️ Rename Server1 (Windows Server 2016)
1. **Windows Icon → Server Manager → Local Server**  
   ![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)  
   ![Local Server](https://github.com/user-attachments/assets/35041124-0049-4ef9-b1ad-7ce98d523cb3)

2. Edit **Computer Name** → Rename as `Server1`.  
   ![Rename](https://github.com/user-attachments/assets/8ec9814d-7653-4885-9b43-993d920f67ef)

---

### 🖥️ Rename Server2 (Windows Server 2016)
1. **Windows Icon → Server Manager → Local Server**  
   ![Server Manager](https://github.com/user-attachments/assets/d3a2401f-5f9e-4b78-8d00-45258753649d)  
   ![Local Server](https://github.com/user-attachments/assets/fe288e4c-75b4-42b0-aeb7-6377b4b068e7)

2. Edit **Computer Name** → Rename as `Server2`.  
   ![Rename](https://github.com/user-attachments/assets/a4b16b7e-f173-430a-9cc8-ad5aee33b2b4)

---

## 🔹 Step 6: Configure IP Address – Client
1. Press **Win + R → ncpa.cpl**  
   ![Network Connections](https://github.com/user-attachments/assets/29eae156-ad70-4dc5-bbb4-e414ad1db5ed)

2. Right-click **Ethernet0 → Properties**  
   ![Ethernet Properties](https://github.com/user-attachments/assets/c1c7e04c-99fa-49f7-9b7a-2cae1586adbc)

3. Select **IPv4 → Properties**  
   ![IPv4 Properties](https://github.com/user-attachments/assets/b8ce0b69-04a7-4c27-9953-208a985f0c2b)

4. Assign manually:  
   - IP: `192.168.10.3`  
   - Subnet: `255.255.255.0`  
   - DNS: `192.168.10.1`  
   ![Configured IP](https://github.com/user-attachments/assets/1de1e765-e6ca-491e-82d5-e0b785ca8304)

---

## 🔹 Step 7: Configure IP Address – Server1
1. **Server Manager → Local Server → Ethernet0**  
   ![Ethernet](https://github.com/user-attachments/assets/637bde5d-1848-467c-85b5-e2ecc077daeb)

2. Edit **IPv4 Properties** → Assign:  
   - IP: `192.168.10.1`  
   - Subnet: `255.255.255.0`  
   ![Configured IP](https://github.com/user-attachments/assets/e356cc45-167d-4666-b330-7a523895981d)

---

## 🔹 Step 8: Configure IP Address – Server2
1. **Server Manager → Local Server → Ethernet0**  
   ![Ethernet](https://github.com/user-attachments/assets/3cf92625-17fd-4c10-94fc-794841f513b5)

2. Edit **IPv4 Properties** → Assign:  
   - IP: `192.168.10.2`  
   - Subnet: `255.255.255.0`  
   - DNS: `192.168.10.1`  
   ![Configured IP](https://github.com/user-attachments/assets/f2c40f48-854d-49cf-ae9c-498f87fb6d80)

---

## 🔹 Step 9: Configure VMware Network (All VMs)
- Open **VM Settings → Network Adapter → Custom → VMnet1 (Host-Only)**  
- Apply the same for **Client, Server1, Server2**.  

Example:  
<img width="1919" height="1079" alt="Screenshot 2025-09-11 093017" src="https://github.com/user-attachments/assets/fd3345ed-d56f-40ee-af2f-8c29ed551aad" />

![VMnet1](https://github.com/user-attachments/assets/8dcda7be-3d83-47de-93f7-a0eb87ab5f5e)

---

## 🔹 Step 10: Disable Firewall (Testing Purpose Only ⚠️)

### Client (Windows 10)
1. **Settings → Network & Internet → Windows Firewall**  
   ![Firewall](https://github.com/user-attachments/assets/3940e4b1-c9f6-415c-bfa3-0ede202a7c0f)  
   ![Turn Off](https://github.com/user-attachments/assets/9f438b63-aef9-4a16-9240-7dbae979e926)

2. Turn off **Public, Private, Domain firewall**.

---

### Server1 & Server2 (Windows Server 2016)
1. **Server Manager → Local Server → Windows Firewall**  
   ![Firewall](https://github.com/user-attachments/assets/73efe095-b9bc-415b-a513-17afe1f894b3)

2. Click **Turn Windows Firewall on/off**.  
3. Disable **Private + Public Firewall**.  
   ![Firewall Off](https://github.com/user-attachments/assets/ad4047c8-0fde-4596-b159-1398a46e8951)

---

## 🔹 Step 11: Test Connectivity (Ping)

### On Client
1. Open **Command Prompt**.  
   ![CMD](https://github.com/user-attachments/assets/68bdbc25-51b6-486f-8e6f-8eb01c48dd4f)

2. Test ping:  
   ```
   ping 192.168.10.1   # Server1
   ```
   <img width="1916" height="1011" alt="image" src="https://github.com/user-attachments/assets/d6bc7066-35dd-46c9-afbb-16951ef8bc40" />
   
```
ping 192.168.10.2   # Server2
```
<img width="1919" height="1007" alt="image" src="https://github.com/user-attachments/assets/0ceb4e70-75e1-40c5-81a0-372f604cc7ac" />


