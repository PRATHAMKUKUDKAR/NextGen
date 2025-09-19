# 🖧 DNS Configuration – Forward Lookup, Reverse Lookup, PTR, CNAME & Secondary Zone

This guide explains how to configure DNS Zones in **Windows Server (Server Manager)** with step-by-step instructions and screenshots.

---

## 📌 Step 1: Open Server Manager
1. Click on **Windows Start Button**.  
2. Select **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)

---

## 📌 Step 2: Open DNS Management
1. Go to **Server Manager → Tools → DNS**.  

---

# 🌐 Forward Lookup Zone

### 🔹 About
- Maps **Domain Name → IP Address**.  
- Most common DNS zone used on the internet.  
- Record types used:  
  - **A Record** → Maps domain name to IPv4 address.  
  - **AAAA Record** → Maps domain name to IPv6 address.  
  - **CNAME Record** → Alias of another domain name.  
  - **MX Record** → Mail exchange server record.  

👉 **Example:**  
`www.nextgen.com → 192.168.10.1`  

✅ **In short:** Forward Lookup Zone = Domain Name → IP Address  

### 📌 Create Forward Lookup Zone
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b1c95699-4dd5-4902-96a0-37c9b49600bb" />

---

# 🔄 Reverse Lookup Zone

### 🔹 About
- Maps **IP Address → Domain Name**.  
- Performs the reverse function of forward lookup.  
- Record type used:  
  - **PTR Record (Pointer Record)** → Maps IP address back to hostname.  

👉 **Example:**  
`192.168.10.1 → www.nextgen.com`  

✅ **In short:** Reverse Lookup Zone = IP Address → Domain Name  

### 📌 Step 3: Create Reverse Lookup Zone
1. Right-click on **Reverse Lookup Zone** → Click **New Zone**  
2. Select **Primary Zone → Next**  
3. Select **IPv4 Reverse Lookup Zone → Next**  
4. Enter **Network ID** → `192.168.10` → Next  
5. Zone folder created → `10.168.192.in-addr.arpa`  
6. Click **Finish**  

📸 Example screenshots:  
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/ac760ae0-b431-4384-afd9-8d52f79fef2d" />  

---

## 📘 Primary Zone
- Contains the **master copy** of DNS records (read/write).  
- Acts as the **authoritative source** for its domain namespace.  
- Only one **Primary Zone** exists per namespace.  
- Stores records like **A, CNAME, MX, PTR, SRV** etc.  
- Changes (add, modify, delete) are allowed only here.  
- Can replicate data to **Secondary Zones**.  

---

# 📘 DNS Record – CNAME (Alias Record)

### 🔹 What is CNAME?
- CNAME = **Alias record** (nickname for another domain).  
- Points one domain name to another domain name.  

👉 **Example:**  
- `www.example.com → example.com`  
- `mail.example.com → server1.example.com`  

✅ **In short:** CNAME = Different names → Same server  

### 📌 Step 4: Create CNAME Record
1. Right-click on domain (e.g., `microsoft.com`) → **New Alias (CNAME)**  
2. Enter alias name → e.g., `HR`  
3. Browse and select **Client1** from Forward Lookup Zone  
4. Confirm → FQDN = `HR.microsoft.com` → OK  
5. Now `HR` points to `Client1`  

📸 Example screenshot:  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f6a3802f-3b68-47d1-abe8-75f3110fbe1f" />

---

# 📘 Secondary Zone

### 🔹 What is Secondary Zone?
- A **read-only copy** of the Primary Zone.  
- Gets data via **Zone Transfer** from Primary.  
- Provides **Redundancy & Load Balancing**.  
- Cannot be edited directly (read-only).  
- Useful for **fault tolerance** (if Primary fails, Secondary resolves queries).  

---

## 📌 Step 5: Install DNS Role on Server2
1. Open **Server Manager → Dashboard → Add Roles and Features**  
2. Select **Role-based installation → Next**  
3. Choose Server2 → Next  
4. Select **DNS Server → Add Features**  
5. Continue → Next → Install  
6. Wait for installation → Close  

📸 Example screenshot:  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/be6a5d57-5051-4c15-8db5-ea066ad9f3aa" />

---

## 📌 Step 6: Create Secondary Zone on Server2
1. Open **DNS Manager** → Expand **Server2**  
2. Right-click **Forward Lookup Zones → New Zone**  
3. Select **Secondary Zone → Next**  
4. Enter zone name → `microsoft.com`  
5. Enter Primary DNS IP → `192.168.10.1`  
6. Click **Finish**  

📸 Example screenshot:  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3ac9ddb7-1ba1-4664-905e-892da1b7aeed" />

---

## 📌 Step 7: Allow Zone Transfer on Server1
1. Go to **Server1 → DNS Manager → Forward Lookup Zones → microsoft.com**  
2. Right-click domain → **Properties → Zone Transfers**  
3. Tick **Allow Zone Transfer**  
4. Select **Only the following servers** → Add IP of Server2 (`192.168.10.2`)  
5. Apply → OK  

📸 Example screenshot:  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b8dba37d-1f78-41eb-a426-fdb3cfdf6b04" />

---

## 📌 Step 8: Verify Secondary Zone
1. Go back to **Server2 DNS Manager**  
2. Refresh Forward Lookup Zones → `microsoft.com`  
3. Records from Primary will appear.  
4. Note: You cannot add/edit records (read-only).  

📸 Example screenshot:  
<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/4589fabe-f403-4efd-bc77-6cde57a50ac1" />

---

