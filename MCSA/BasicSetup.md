# MCSA Practical – Client (Windows 10) + 2 Servers (Windows Server 2016) Basic Setup

---

## Step 1: Open VMware
- Open **VMware Workstation / VMware Player**.
- Click **Create a New Virtual Machine**.

---

## Step 2: Install Windows 10 (Client)
- Select **ISO image** → Windows 10 ISO.
- Install Windows 10 normally.

---

## Step 3: Install Windows Server 2016 (Server1)
- Create a new VM → use **Windows Server 2016 ISO**.
- Install Windows Server 2016.

---

## Step 4: Install Windows Server 2016 (Server2)
- Create a new VM → use **Windows Server 2016 ISO**.
- Install Windows Server 2016.

---

## Step 5: Rename Devices (VM Names)

### Rename `Client` (Windows 10)
1. Click **Windows Icon** → **Settings**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/b1474db2-85e1-4e6a-8a85-134fd09a6bce" />

2. Click on **System**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/eb174fc2-b344-4114-806d-fc58edb4bacd" />

3. Scroll down → Click on **About**.  
4. Click on **Advanced System Settings**.  
   <img width="1911" height="1006" src="https://github.com/user-attachments/assets/354a0d8e-156e-408a-976c-bab76977b7cb" />

5. Go to **Computer Name** tab.  
6. Enter computer name: **Client**.  

---

### Rename `Server1` (Windows Server 2016)
1. Click **Windows Icon** → **Server Manager**.  
   <img width="1886" height="1005" src="https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc" />

2. Click on **Local Server**.  
3. Click on **Computer Name**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/35041124-0049-4ef9-b1ad-7ce98d523cb3" />

4. Go to **Computer Name** tab.  
5. Enter computer name: **Server1**.  
   <img width="1882" height="1079" src="https://github.com/user-attachments/assets/8ec9814d-7653-4885-9b43-993d920f67ef" />

---

### Rename `Server2` (Windows Server 2016)
1. Click **Windows Icon** → **Server Manager**.  
   <img width="1919" height="1005" src="https://github.com/user-attachments/assets/d3a2401f-5f9e-4b78-8d00-45258753649d" />

2. Click on **Local Server**.  
3. Click on **Computer Name**.  
   <img width="1913" height="1079" src="https://github.com/user-attachments/assets/fe288e4c-75b4-42b0-aeb7-6377b4b068e7" />

4. Go to **Computer Name** tab.  
5. Enter computer name: **Server2**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/a4b16b7e-f173-430a-9cc8-ad5aee33b2b4" />

---

## Step 6: Assign IP Address (Client)
1. Press **Windows Key + R** → type `ncpa.cpl` → click **OK**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/29eae156-ad70-4dc5-bbb4-e414ad1db5ed" />

2. Right-click **Ethernet0** → **Properties**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/c1c7e04c-99fa-49f7-9b7a-2cae1586adbc" />

3. Select **Internet Protocol Version 4 (TCP/IPv4)** → click **Properties**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/b8ce0b69-04a7-4c27-9953-208a985f0c2b" />

4. Configure IP manually:  
   - **IP Address:** `192.168.10.3`  
   - **Subnet Mask:** `255.255.255.0`  
   - **Preferred DNS Server:** `192.168.10.1`  

5. Click **OK**.  
   <img width="1919" height="1069" src="https://github.com/user-attachments/assets/1de1e765-e6ca-491e-82d5-e0b785ca8304" />

---

## Step 7: Assign IP Address (Server1)
1. Open **Server Manager**.  
   <img width="1919" height="1078" src="https://github.com/user-attachments/assets/a11c9a6d-1648-489b-b8d8-f54660c8dd5a" />

2. Click on **Local Server** → select **Ethernet0**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/637bde5d-1848-467c-85b5-e2ecc077daeb" />

3. Open **Properties** → select **Internet Protocol Version 4 (TCP/IPv4)** → click **Properties**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/6e3f8529-d410-406b-ba97-7dc929bcd085" />

4. Configure IP manually:  
   - **IP Address:** `192.168.10.1`  
   - **Subnet Mask:** `255.255.255.0`  

5. Click **OK**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/e356cc45-167d-4666-b330-7a523895981d" />

---

## Step 8: Assign IP Address (Server2)
1. Open **Server Manager**.  
   <img width="1919" height="1079" src="https://github.com/user-attachments/assets/8f57a562-5ea9-4426-ab73-8aeb01df44dc" />

2. Click on **Local Server** → select **Ethernet0**.  
   <img width="1899" height="1075" src="https://github.com/user-attachments/assets/3cf92625-17fd-4c10-94fc-794841f513b5" />

3. Open **Properties** → select **Internet Protocol Version 4 (TCP/IPv4)** → click **Properties**.  
   <img width="1917" height="1079" src="https://github.com/user-attachments/assets/e86c97c4-f333-488a-9c80-19d0fee55573" />

4. Configure IP manually:  
   - **IP Address:** `192.168.10.2`  
   - **Subnet Mask:** `255.255.255.0`  
   - **Preferred DNS Server:** `192.168.10.1`  

5. Click **OK**.  
   <img width="1919" height="1076" src="https://github.com/user-attachments/assets/f2c40f48-854d-49cf-ae9c-498f87fb6d80" />
