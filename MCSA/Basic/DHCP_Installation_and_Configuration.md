# 📘 DHCP Installation and Configuration on Server1

---

## 🔹 Part 1: Install DHCP Role

### Step 1: Open Server Manager
1. Click on **Windows Start Button**.  
2. Select **Server Manager**.  

 ![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)  
 
---

### Step 2: Add DHCP Role
1. In Server Manager → click **Add roles and features**.  
2. Click **Next** until you reach **Server Roles**.  
3. Tick ✅ **DHCP Server**.  

![Add DHCP](https://github.com/user-attachments/assets/a380a22b-bc6b-4c00-82fd-9b9ef9e908a0)

4. Click **Add Features** → **Next**.  
5. Continue clicking **Next** until **Confirmation** page.  
6. Tick ✅ **Restart the destination server automatically if required**.  
7. Click **Install**.  

![Install DHCP](https://github.com/user-attachments/assets/ef1630d9-cee8-4135-98f3-9b6ed951290c)

---

### Step 3: Complete DHCP Installation
1. Wait for installation to finish.  
2. Click **Close**.  
3. In Server Manager, click the **Flag Icon**.  
4. Select **Complete DHCP configuration**.  

![DHCP Config](https://github.com/user-attachments/assets/0689ed90-d1a2-4d82-b7df-a5607f5225f6)

5. Click **Next → Commit → Close**.  

✅ DHCP Role is successfully installed.

---

## 🔹 Part 2: Configure DHCP

### Step 1: Open DHCP Management
1. Go to **Server Manager → Tools → DHCP**.  

![Open DHCP](https://github.com/user-attachments/assets/27c30107-81b9-4ae8-826b-62f7ce7eceac)

---

### Step 2: Create New Scope
1. Expand your server → Right-click **IPv4** → Select **New Scope**.  
2. Click **Next**.  
3. Enter Scope Name → `MicrosoftDomain`.  

![Scope Name](https://github.com/user-attachments/assets/7d8f1ff4-84a9-4597-9b86-39626b1ecaa5)

---

### Step 3: Set IP Address Range
- Start IP: `192.168.10.11`  
- End IP: `192.168.10.20`  

![IP Range](https://github.com/user-attachments/assets/a630a92b-223e-42ab-ab04-6b8667752ea4)

---

### Step 4: Add Exclusions
- Start IP: `192.168.10.12`  
- End IP: `192.168.10.13`  

![Exclusions](https://github.com/user-attachments/assets/0578ac16-551a-4ae3-8460-14a5c6507190)

---

### Step 5: Lease Duration
- Leave default → Click **Next**.  

![Lease Duration](https://github.com/user-attachments/assets/12eef570-7b82-4caa-b5bc-3349db9254e0)

---

### Step 6: Configure DHCP Options
- Select **Yes, I want to configure these options now** → Next.  

![Config Options](https://github.com/user-attachments/assets/acaabcc3-4416-43d6-8ac5-d2382c2abb01)

---

### Step 7: Router (Default Gateway)
- IP: `192.168.10.254`  
- Click **Add → Next**.  

![Gateway](https://github.com/user-attachments/assets/843e174b-b448-457c-8b13-568c66a56788)

---

### Step 8: DNS & WINS
- Keep default DNS (your server’s IP).  
- Click **Next** for DNS and WINS configuration.  

---

### Step 9: Activate Scope
- Select **Yes, I want to activate this scope now** → Next → Finish.  

![Activate Scope](https://github.com/user-attachments/assets/a862f183-a8a8-44b3-88d4-812e5f4292b4)

✅ DHCP Scope is successfully configured.

---

## 🔹 Part 3: Verify DHCP on Server2

### Step 1: Open Command Prompt
1. Press **Windows + R** → type `cmd` → OK.  

![CMD](https://github.com/user-attachments/assets/68203c03-e563-4eac-a790-71e05761a907)

---

### Step 2: Check IP Address
1. Type:  
   ```
   ipconfig
   ```
2. Verify that client received IP from DHCP range 192.168.10.11 - 192.168.10.20.

<img width="1919" height="1000" alt="Screenshot 2025-09-18 170647" src="https://github.com/user-attachments/assets/2124b2d0-03a4-4961-9923-aadbf772066a" />
