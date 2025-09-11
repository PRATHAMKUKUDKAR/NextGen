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

## Step 9: Same virtual Network IN all Client server1 server2
### client
1. Click on right click on Client
2. click on client
3. Go to setting
<img width="1919" height="1079" alt="Screenshot 2025-09-11 085741" src="https://github.com/user-attachments/assets/867ea8d7-6a8b-4542-96f8-677a053dba1c" />
4. Ckick on network Adaptor
5. click on custome: specific vertual network
6. select VMNET1
7. CLICK ON OK
<img width="1919" height="1079" alt="Screenshot 2025-09-11 090710" src="https://github.com/user-attachments/assets/8dcda7be-3d83-47de-93f7-a0eb87ab5f5e" />

### Server1
1. Click on right click on Server1
2. click on Server1
3. Go to setting

<img width="1919" height="1079" alt="Screenshot 2025-09-11 091231" src="https://github.com/user-attachments/assets/6aceb47c-0bbf-4a99-8832-a89cbc911157" />


5. Ckick on network Adaptor
6. click on custome: specific vertual network
7. select VMNET1
8. CLICK ON OK

<img width="1919" height="1079" alt="Screenshot 2025-09-11 092504" src="https://github.com/user-attachments/assets/88ebddc0-9c01-4ef3-8405-3e97cc04f47b" />

### Server2
1. Click on right click on Server2
2. click on Server2
3. Go to setting

<img width="1919" height="1079" alt="Screenshot 2025-09-11 093017" src="https://github.com/user-attachments/assets/398a0936-a297-4d26-a0c9-64e060efb6b2" />



5. Ckick on network Adaptor
6. click on custome: specific vertual network
7. select VMNET1
8. CLICK ON OK

<img width="1919" height="1079" alt="Screenshot 2025-09-11 093252" src="https://github.com/user-attachments/assets/63e83c58-29be-4845-83d2-cdb15c5c14ff" />


## Step 10: Disable Firewall (for Testing)

### Client
1. click on window icon
2. go to setting

<img width="1919" height="1077" alt="Screenshot 2025-09-11 102858" src="https://github.com/user-attachments/assets/3940e4b1-c9f6-415c-bfa3-0ede202a7c0f" />

3. click on networkand internet
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d9ac4188-23f3-4cdc-b082-2ba398589c4c" />

4. scroll down and click window firewall

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5f7aa024-e069-46a7-99ab-91b5628233d1" />

5. trun of public private and domain firewall 
<img width="1919" height="1079" alt="Screenshot 2025-09-11 104231" src="https://github.com/user-attachments/assets/9f438b63-aef9-4a16-9240-7dbae979e926" />


### server1
1. click on window icon
2. click on server manager
3. 
<img width="1892" height="1079" alt="Screenshot 2025-09-11 094441" src="https://github.com/user-attachments/assets/43b91962-3851-4a8c-b2d6-b6ca2096e3ce" />

4. click on local server
5. click on window firewall

<img width="1919" height="1079" alt="Screenshot 2025-09-11 094934" src="https://github.com/user-attachments/assets/73efe095-b9bc-415b-a513-17afe1f894b3" />

6.click turn window firewall on or of
<img width="1919" height="1079" alt="Screenshot 2025-09-11 095302" src="https://github.com/user-attachments/assets/8a9c7354-746e-4876-b231-038fa013e101" />

7. trurn of private network setting and public netwoek setting
<img width="1919" height="1003" alt="Screenshot 2025-09-11 095753" src="https://github.com/user-attachments/assets/ad4047c8-0fde-4596-b159-1398a46e8951" />


### server2
1. click on window icon
2. click on server manager

<img width="1917" height="1079" alt="Screenshot 2025-09-11 100437" src="https://github.com/user-attachments/assets/8a6dc832-2e84-4eee-a780-0ecfe3b6f06c" />


4. click on local server
5. click on window firewall
<img width="1919" height="1079" alt="Screenshot 2025-09-11 100816" src="https://github.com/user-attachments/assets/d062179c-a204-479b-9edc-a995e1f9b1ae" />


6.click turn window firewall on or of

<img width="1919" height="1079" alt="Screenshot 2025-09-11 101205" src="https://github.com/user-attachments/assets/77427035-ed89-4322-86e9-f0383333406e" />


7. trurn of private network setting and public netwoek setting

<img width="1919" height="1079" alt="Screenshot 2025-09-11 101451" src="https://github.com/user-attachments/assets/6b229eab-1cc9-4e7c-9908-6e7d4d12524c" />

## Step 11: Test Connectivity (Ping)
### On client
1. click on window icon
2. click on tyepe hare to search: command prompt
click on command prompt
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/68bdbc25-51b6-486f-8e6f-8eb01c48dd4f" />

