# 🖥️ MCSA Practical – Client (Windows 10) + 2 Servers (Windows Server 2016)

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
- Create new VM → use **Windows Server 2016 ISO**.
- Install Windows Server 2016.

---

## Step 4: Install Windows Server 2016 (Server2)
- Create new VM → use **Windows Server 2016 ISO**.
- Install Windows Server 2016.

---

## Step 5: Rename Devices (VM Names)

### 🔹 Rename `Client` (Windows 10)
1. Click on **Windows Icon** → **Settings**.  
   <img width="1919" height="1079" alt="Screenshot 2025-09-10 153108" src="https://github.com/user-attachments/assets/b1474db2-85e1-4e6a-8a85-134fd09a6bce" />

2. Click on **System**.  
   <img width="1919" height="1079" alt="Screenshot 2025-09-10 153722" src="https://github.com/user-attachments/assets/eb174fc2-b344-4114-806d-fc58edb4bacd" />

3. Scroll down → Click on **About**.  
4. Click on **Advanced System Settings**.  
   <img width="1911" height="1006" alt="Screenshot 2025-09-10 215720" src="https://github.com/user-attachments/assets/354a0d8e-156e-408a-976c-bab76977b7cb" />

5. Go to **Computer Name** tab.  
6. Enter computer description/name: `Client`.

---

### 🔹 Rename `Server1` (Windows Server 2016)
1. Click on **Windows Icon** → **Server Manager**.  
   <img width="1886" height="1005" alt="Screenshot 2025-09-10 222950" src="https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc" />

2. Click on **Local Server**.  
3. Click on **Computer Name**.  
   <img width="1919" height="1079" alt="Screenshot 2025-09-10 223337" src="https://github.com/user-attachments/assets/35041124-0049-4ef9-b1ad-7ce98d523cb3" />

4. Go to **Computer Name** tab.  
5. Enter computer description/name: `Server1`.  
   <img width="1882" height="1079" alt="Screenshot 2025-09-10 223714" src="https://github.com/user-attachments/assets/8ec9814d-7653-4885-9b43-993d920f67ef" />

---

### 🔹 Rename `Server2` (Windows Server 2016)
1. Click on **Windows Icon** → **Server Manager**.  
   <img width="1919" height="1005" alt="Screenshot 2025-09-10 224542" src="https://github.com/user-attachments/assets/d3a2401f-5f9e-4b78-8d00-45258753649d" />

2. Click on **Local Server**.  
3. Click on **Computer Name**.  
   <img width="1913" height="1079" alt="Screenshot 2025-09-10 231245" src="https://github.com/user-attachments/assets/fe288e4c-75b4-42b0-aeb7-6377b4b068e7" />

4. Go to **Computer Name** tab.  
5. Enter computer description/name: `Server2`.  
   <img width="1919" height="1079" alt="Screenshot 2025-09-10 231631" src="https://github.com/user-attachments/assets/a4b16b7e-f173-430a-9cc8-ad5aee33b2b4" />

---

## Step 6: Assign IP Addresses
Go inside each VM → open **Network Settings** → set static IPs:

- **Client (Windows 10)**
