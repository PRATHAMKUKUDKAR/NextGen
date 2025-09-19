# 📘 DNS Configuration in Windows Server  

This document explains **DNS Zones** (Forward, Reverse, Primary, Secondary, CNAME) with **step-by-step configuration** and **screenshots**.  

---

## 🚀 Step 1: Open Server Manager  
1. Click on **Windows Start Button**.  
2. Select **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)  

---

## 🌐 Forward Lookup Zone  

### 🔹 What it does:  
- Maps **Domain Name → IP Address**.  
- Most common DNS zone used on the internet.  
- Record types:  
  - **A Record** → Maps domain to IPv4  
  - **AAAA Record** → Maps domain to IPv6  
  - **CNAME Record** → Alias  
  - **MX Record** → Mail server  

✅ Example: `www.nextgen.com → 192.168.10.1`  

---

### ✅ Steps to Configure Forward Lookup Zone  
1. Go to **Server Manager → Tools → DNS**.  
2. Right-click on **Forward Lookup Zones → New Zone**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/b1c95699-4dd5-4902-96a0-37c9b49600bb" />  

---

## 🔄 Reverse Lookup Zone  

### 🔹 What it does:  
- Maps **IP Address → Domain Name**.  
- Uses **PTR Record (Pointer Record)**.  
- Helps in:  
  - Email server verification  
  - Network troubleshooting  
  - Security auditing  

✅ Example: `192.168.10.1 → www.nextgen.com`  

---

## 🛠️ Primary Zone 
- Master copy of DNS records (read/write).  
- Authoritative for domain namespace.  
- Stores **A, CNAME, MX, PTR** records.  
- Replicates to Secondary Zones.  

---

### ✅ Steps to Configure Reverse Lookup Zone  
1. Right-click on **Reverse Lookup Zones → New Zone**.  
2. Click **Next**.  

<img width="1919" height="1078" src="https://github.com/user-attachments/assets/ac760ae0-b431-4384-afd9-8d52f79fef2d" />  

3. Select **Primary Zone → Next**.  

<img width="1919" height="1068" src="https://github.com/user-attachments/assets/a2c22c55-5b37-49d4-bd5f-54b969d104aa" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/1d47d2ef-d372-4b4f-bae6-56565e5649d6" />  

4. Select **IPv4 Reverse Lookup Zone → Next**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/fd819836-361b-4d09-a0f9-41c4060b3bbc" />  

5. Enter **Network ID: 192.168.10 → Next**.  

<img width="1897" height="1079" src="https://github.com/user-attachments/assets/aadf7f70-7a80-4aef-8494-6b12c567e753" />  

6. A folder will be created automatically: **10.168.192.in-addr.arpa**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/7122cd02-0c68-4d70-b1eb-0f1fdf410f8e" />  

7. Click **Next → Finish**.  

<img width="1899" height="1062" src="https://github.com/user-attachments/assets/58db2e03-6d02-4fd4-bb8f-6ba7fa56852e" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/275d44cc-8906-499d-8b89-c3d3aff9fd55" />  

8. Go to **microsoft.com → Properties**.  

<img width="1919" height="1075" src="https://github.com/user-attachments/assets/aa8b5252-3792-46bd-afe5-0e44969b23e6" />  

9. Tick/untick **Update associated PTR record** to refresh.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/26df434c-ea50-4f75-b13b-ae06a58d0ad4" />  

10. Check Reverse Lookup Zone folder → You’ll see `10.168.192.in-addr.arpa`.  

<img width="1884" height="1079" src="https://github.com/user-attachments/assets/8f5bc800-2ab4-49ba-b06f-6ea547c8d918" />  

---


## 📘 Secondary Zone  

### 🔹 What is Secondary Zone?  
- A **read-only copy** of the Primary Zone.  
- Updated through **Zone Transfer**.  
- Provides **redundancy + load balancing**.  
- Cannot be edited directly.  

✅ In short: **Backup of Primary Zone (Read-only)**  

---

### ✅ Steps to Configure Secondary Zone (Server2)  

1. Open **Server Manager → Add Roles → DNS Server**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/4af2e8e5-4fc2-416d-b51b-29b86fc45de9" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/7d428674-9f52-4c03-a887-0a1aadc53413" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/252eb246-160b-46bd-b406-46a3d28d971d" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/be6a5d57-5051-4c15-8db5-ea066ad9f3aa" />  

2. Open **DNS Tool → Forward Lookup Zones → New Zone**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/21a02ace-0af2-4109-b8b1-d9409044a1f5" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/3ac9ddb7-1ba1-4664-905e-892da1b7aeed" />  

3. Select **Secondary Zone → Next → microsoft.com → Master IP 192.168.10.1 → Finish**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/5f85b683-2f6a-41ba-80e0-c5612a3374ac" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/4d16d7c8-235f-4d29-b52e-f32e15f38750" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/03382e0a-33a6-4980-a42e-d96660655e14" />  

4. Initially shows error → **Zone not loaded**.  

<img width="1916" height="1002" src="https://github.com/user-attachments/assets/0d409fd2-37d6-4a13-ba4a-a6e8898fc012" />  

---

### ✅ Allow Zone Transfer (Server1)  
1. Right-click **microsoft.com → Properties → Zone Transfer**.  
2. Tick **Allow zone transfer → Only to the following servers → Add IP 192.168.10.2**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/732ec4e9-7ecb-49b7-8344-f179866b321b" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/930d4997-3d76-480a-8c44-76d2680a2399" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/b8dba37d-1f78-41eb-a426-fdb3cfdf6b04" />  

3. Refresh → Now records load on Server2.  

<img width="1919" height="1010" src="https://github.com/user-attachments/assets/8bb3f019-f372-43b4-bb5e-3f963cd4e3a1" />  

👉 Note: Server2 cannot create new zones/records (read-only).  

<img width="1919" height="1006" src="https://github.com/user-attachments/assets/4589fabe-f403-4efd-bc77-6cde57a50ac1" />  

---

## 📘 DNS Record – CNAME (Alias Record)  

### 🔹 What is CNAME?  
- CNAME = Alias record (nickname for another domain).  
- Points **one domain → another domain**.  

✅ Example: `HR.microsoft.com → client1.microsoft.com`  

---

### ✅ Steps to Configure CNAME  
1. Right-click **microsoft.com → New Alias (CNAME)**.  

<img width="1908" height="1079" src="https://github.com/user-attachments/assets/d30f105f-c21e-4922-8e4a-03f8db54b0b5" />  

2. Type alias name → `HR`.  

<img width="1919" height="1059" src="https://github.com/user-attachments/assets/d97140d6-96ce-4be8-a369-270b7a0bdc4a" />  

3. Browse → Select **Client1.microsoft.com**.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/7d214b0c-8161-43ee-a0a4-2f50d4ab9be6" />  
<img width="1919" height="1079" src="https://github.com/user-attachments/assets/27925fba-6e79-44fb-b925-6bd03a3ce16c" />  

4. Verify alias created.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/f6a3802f-3b68-47d1-abe8-75f3110fbe1f" />  

5. Test alias: `Win + R → \\HR → OK`.  

<img width="1919" height="1079" src="https://github.com/user-attachments/assets/b0d4bea4-7293-4042-a83f-9df2f1419db3" />  
<img width="1919" height="1010" src="https://github.com/user-attachments/assets/ac8cd3ab-d3de-401f-8e48-0571403238c8" />  

---

