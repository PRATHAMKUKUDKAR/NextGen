# 🖧 DNS Configuration – Forward Lookup, Reverse Lookup, PTR & CNAME

This guide explains how to configure DNS Zones in **Windows Server (Server Manager)** with step-by-step instructions and screenshots.

---

## 📌 Step 1: Open Server Manager
1. Click on **Windows Start Button**.  
2. Select **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)

---

## 📌 Step 2: Open DNS Management
1. Go to **Server Manager → Tools → DNS**.  

### Forward Lookup Zone
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b1c95699-4dd5-4902-96a0-37c9b49600bb" />

---

# 🌐 Forward Lookup Zone

- Maps **Domain Name → IP Address**.  
- Most common DNS zone used on the internet.  
- Record types used:  
  - **A Record** → Maps domain name to IPv4 address.  
  - **AAAA Record** → Maps domain name to IPv6 address.  
  - **CNAME Record** → Alias of another domain name.  
  - **MX Record** → Mail exchange server record.  
- Essential for browsing websites, accessing services, and resolving domain names.  

👉 **Example:**  
`www.nextgen.com → 192.168.10.1`  

✅ **In short:** Forward Lookup Zone = Domain Name → IP Address  

---

# 🔄 Reverse Lookup Zone

- Maps **IP Address → Domain Name**.  
- Performs the reverse function of forward lookup.  
- Record type used:  
  - **PTR Record (Pointer Record)** → Maps IP address back to hostname.  
- Helps in:  
  - **Network troubleshooting** (ping, nslookup, traceroute).  
  - **Email server verification** (anti-spam reverse DNS checks).  
  - **Security auditing** (verify IP belongs to valid domain).  

👉 **Example:**  
`192.168.10.1 → www.nextgen.com`  

✅ **In short:** Reverse Lookup Zone = IP Address → Domain Name  

---

## 📌 Step 3: Create Reverse Lookup Zone
1. Right-click on **Reverse Lookup Zone**  
2. Click **New Zone**  

<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/ac760ae0-b431-4384-afd9-8d52f79fef2d" />

3. Click **Next**  
<img width="1919" height="1068" alt="image" src="https://github.com/user-attachments/assets/a2c22c55-5b37-49d4-bd5f-54b969d104aa" />

4. Tick **Primary Zone** → Click **Next**  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1d47d2ef-d372-4b4f-bae6-56565e5649d6" />

---

## 📘 DNS Zones Under Reverse Lookup Zone – Primary

- Contains the **master copy** of DNS records (read/write).  
- Acts as the **authoritative source** for its domain namespace.  
- Only one **Primary Zone** exists per DNS namespace.  
- Stores records like **A, CNAME, MX, PTR, SRV** etc.  
- Changes (add, modify, delete records) can be made **only here**.  
- Can replicate data to **Secondary Zones** for redundancy.  

---

## 📌 Step 4: Configure Reverse Lookup Zone
1. Select **IPv4 Reverse Lookup Zone** → Click **Next**  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/fd819836-361b-4d09-a0f9-41c4060b3bbc" />

2. Type Network ID → `192.168.10` → Click **Next**  
<img width="1897" height="1079" alt="image" src="https://github.com/user-attachments/assets/aadf7f70-7a80-4aef-8494-6b12c567e753" />

3. Zone folder automatically created → `10.168.192.in-addr.arpa`  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7122cd02-0c68-4d70-b1eb-0f1fdf410f8e" />

4. Click **Next → Finish**  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/275d44cc-8906-499d-8b89-c3d3aff9fd55" />

---

## 📌 Step 5: Update PTR Records
1. Right-click on **microsoft.com** → Select **Properties**  
<img width="1919" height="1075" alt="image" src="https://github.com/user-attachments/assets/aa8b5252-3792-46bd-afe5-0e44969b23e6" />

2. Enable/Disable **Update Associated PTR Records** (refresh settings).  
3. Click **OK**.  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/26df434c-ea50-4f75-b13b-ae06a58d0ad4" />

4. Check Reverse Lookup Zone folder (`10.168.192.in-addr.arpa`) → IPs mapped to hostnames.  
<img width="1884" height="1079" alt="image" src="https://github.com/user-attachments/assets/8f5bc800-2ab4-49ba-b06f-6ea547c8d918" />

---

# 📘 DNS Record – CNAME (Alias Record)

## 🔹 What is CNAME?
- CNAME = **Alias record** (nickname for another domain).  
- It points one domain name to another domain name (not directly to an IP).  

## 🔹 Why use CNAME?
- Avoids writing the same IP again and again.  
- If the main domain IP changes, CNAME will still work.  
- Easy to manage multiple names for the same server.  

👉 **Example:**  
- `www.example.com → example.com`  
- `mail.example.com → server1.example.com`  

✅ **In short:** CNAME = Different names → Same server  

---

## 📌 Step 6: Create CNAME Record
1. Right-click on **microsoft.com** → Select **New Alias (CNAME)**  
<img width="1908" height="1079" alt="image" src="https://github.com/user-attachments/assets/d30f105f-c21e-4922-8e4a-03f8db54b0b5" />

2. Type alias name → `HR`  
<img width="1919" height="1059" alt="image" src="https://github.com/user-attachments/assets/d97140d6-96ce-4be8-a369-270b7a0bdc4a" />

3. Browse → Select **Client** from `microsoft.com` forward lookup zone  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7d214b0c-8161-43ee-a0a4-2f50d4ab9be6" />

4. Confirm → Fully Qualified Domain Name = `client1.microsoft.com`  
5. Click **OK**  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/27925fba-6e79-44fb-b925-6bd03a3ce16c" />

6. Now see new **HR Alias (CNAME)** created  
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f6a3802f-3b68-47d1-abe8-75f3110fbe1f" />

---

## 📌 Step 7: Verify CNAME Record
1. Press **Windows + R**  
2. Type → `\\HR`  
3. Click **OK**  

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b0d4bea4-7293-4042-a83f-9df2f1419db3" />

✅ HR (alias) successfully points to **Client**  

<img width="1919" height="1010" alt="image" src="https://github.com/user-attachments/assets/ac8cd3ab-d3de-401f-8e48-0571403238c8" />

---

# 📘 DNS – Secondary Zone

## 🔹 What is a Secondary Zone?
- A **read-only copy** of a Primary Zone.  
- It gets its data through **Zone Transfer** from the Primary DNS server.  
- Provides **redundancy and load balancing** for DNS queries.  
- Cannot be edited directly – only updated from the Primary Zone.  
- Helps in fault tolerance (if Primary goes down, Secondary still resolves queries).

# Configuration
1. Go to server 2
2. click on window icon
3. click on server manager
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3fb90c9e-3aab-4572-ac57-97504c141fd8" />

4. click on Dashbord
5. Add Role and Feature
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4af2e8e5-4fc2-416d-b51b-29b86fc45de9" />

6. click on Dashbord
7. Add Role and Feature
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7d428674-9f52-4c03-a887-0a1aadc53413" />

8. Before You Beguin Click next
9. instaletion Type tick on role base or Feature base installation click Next
10. server Selection click next
11. server Role click on DNS Sever
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/252eb246-160b-46bd-b406-46a3d28d971d" />
12. click on Add Feature
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/59f2b051-913a-4f24-b74b-ec54774ab669" />

13. feature click next
14. dns server click next

15. conformation
16. tick on Restart the destination Server Atomaticaly If requqre
17. click on Yes
18. click on Install
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/be6a5d57-5051-4c15-8db5-ea066ad9f3aa" />
19. after conplite Feture Instalation then click on close
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/c22d3bd0-d512-421d-b8d8-f05bd52432cc" />
Configuration
1. Click on tools
2. then click on Dns
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/31b18622-9e84-409a-a7bb-78d1e71cbc13" />

3. click on Server2
4. clik Forward Lookup Zone folder
5. click New Zone
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/21a02ace-0af2-4109-b8b1-d9409044a1f5" />

6. clik next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e93de1b7-823b-44b4-8948-1a63e27d3f3d" />

zone type 
7. click on secondary zone 
8. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3ac9ddb7-1ba1-4664-905e-892da1b7aeed" />

zone name
9. type Zone name `microsoft.com`
10. click next 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5f85b683-2f6a-41ba-80e0-c5612a3374ac" />

master dns server
11. type ip address `192.168.10.1` 
12. click on next 
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4d16d7c8-235f-4d29-b52e-f32e15f38750" />
13. clik on Finish
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/03382e0a-33a6-4980-a42e-d96660655e14" />

15. clik on forward lookup zonee folder
16. click on microsoft .com
17. the see the error zone not loaded by dns server
<img width="1916" height="1002" alt="image" src="https://github.com/user-attachments/assets/0d409fd2-37d6-4a13-ba4a-a6e8898fc012" />

approwal on serve1
1. go to forward lookup zone
2. right click on microsoft.co
3. click on properties
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/732ec4e9-7ecb-49b7-8344-f179866b321b" />


4. click on zone trasfare
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/930d4997-3d76-480a-8c44-76d2680a2399" />

5. tick allow zone transfer
6. tick on only the following servers
7. click on Edit
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b8dba37d-1f78-41eb-a426-fdb3cfdf6b04" />


8. type ip address
9. click ok
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/87021d90-2cad-493d-8081-8b80b0c60d7e" />

10. right click on microsoft.com
11. click on Refresh
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bea22d31-6296-4ea5-89a6-95d849c024d3" />

