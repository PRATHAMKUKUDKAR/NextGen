# 🖥️ Workgroup vs Domain in Windows Networking

## 🔹 Workgroup
A **Workgroup** is a peer-to-peer network model where each computer is responsible for its own security and management.  

### ✨ Features:
- No centralized control (each PC manages itself).  
- User accounts are local to each computer.  
- Best suited for **small networks** (≤10 PCs).  
- No domain controller required.  
- Simple setup, usually for home or small offices.  

---

## 🔹 Domain
A **Domain** is a client-server network model managed by a **Domain Controller (DC)**.  

### ✨ Features:
- Centralized management of users, computers, and policies.  
- Users can log in to **any PC in the domain** with a single account.  
- Best suited for **large networks** (corporates, universities).  
- Provides advanced security and group policies.  
- Requires at least one **Domain Controller (Windows Server)**.  

---

## 🔁 Key Differences

| Feature              | Workgroup | Domain |
|----------------------|-----------|--------|
| **Management**       | Each PC manages itself | Centralized via Domain Controller |
| **User Accounts**    | Local on each PC | Stored in Domain Controller |
| **Security**         | Basic, local only | Advanced (Group Policies, Permissions, Encryption) |
| **Scalability**      | Small networks | Large networks |
| **Authentication**   | Local PC login | Domain login (single account across network) |
| **Best For**         | Home / small office | Corporate / enterprise networks |

---
# 💾 NTFS vs FAT32 File System

## 📌 Overview
Windows operating systems support multiple file systems.  
The two most commonly used are **NTFS (New Technology File System)** and **FAT32 (File Allocation Table 32)**.  
Each has its own strengths and limitations.

---

## 🔹 NTFS (New Technology File System)

### ✨ Features:
- Introduced with **Windows NT**.  
- Supports **very large files** (up to 16 TB+ depending on cluster size).  
- Provides **file and folder security** with permissions.  
- Supports **encryption (EFS)** and **compression**.  
- More reliable due to **journaling** (tracks changes to avoid corruption).  
- Commonly used for **Windows system drives** and large storage.  

---

## 🔹 FAT32 (File Allocation Table 32)

### ✨ Features:
- Introduced with **Windows 95 OSR2**.  
- Maximum file size: **4 GB**.  
- Maximum partition size: **2 TB**.  
- No file-level security or encryption.  
- Supported across **Windows, Linux, macOS, consoles, and embedded devices**.  
- Best for **USB drives and cross-platform compatibility**.  

---

## 🔁 Key Differences

| Feature              | NTFS | FAT32 |
|----------------------|------|-------|
| **Full Form**        | New Technology File System | File Allocation Table 32 |
| **Introduced In**    | Windows NT (1993) | Windows 95 OSR2 (1996) |
| **Max File Size**    | 16 TB – 256 TB (depends) | 4 GB |
| **Max Partition**    | 256 TB | 2 TB |
| **Security**         | File/folder permissions, encryption | None |
| **Reliability**      | Journaling (less data loss) | No journaling |
| **Compression**      | Supported | Not supported |
| **Encryption**       | Supported (EFS) | Not supported |
| **Compatibility**    | Modern Windows (limited Linux/macOS) | Almost all OS & devices |
| **Best For**         | Internal/system drives | USB drives, cross-platform use |

---



# 🌐 DNS vs NetBIOS  

## 🔹 DNS (Domain Name System)
- Converts **domain names → IP addresses**.  
- Example: `www.microsoft.com` → `20.112.52.29`  
- Works on **Internet** and modern networks.  
- Uses **hierarchical structure** (Root → TLD → Domain).  
- Port: **53 (UDP/TCP)**.  
- Fast, scalable, and global.  

✅ **Best for:** Internet, large networks, websites.  

---

## 🔹 NetBIOS (Network Basic Input/Output System)
- Converts **computer names → IP addresses** in a LAN.  
- Example: `\\SERVER1` → `192.168.1.10`  
- Works on **local networks (LAN)** only.  
- Flat name system (no hierarchy).  
- Port: **137, 138, 139**.  
- Old technology, mostly replaced by **DNS + Active Directory**.  

✅ **Best for:** Small local networks, legacy systems.  

---

## ⚖️ Difference
| Feature           | DNS 🌍 | NetBIOS 🖥️ |
|-------------------|--------|-------------|
| Usage             | Internet & LAN | Only LAN |
| Naming System     | Hierarchical   | Flat (single level) |
| Port              | 53             | 137–139 |
| Speed & Scalability | High | Limited |
| Status            | Modern, still used | Legacy, less used |

---
# 🌐 DNS Record Types

DNS (Domain Name System) uses different record types to map names with IPs or services.  

---

## 🔹 1. A Record (Address Record)
- Maps a **domain name → IPv4 address**.  
- Example: `www.example.com → 192.168.10.1`

---

## 🔹 2. AAAA Record
- Maps a **domain name → IPv6 address**.  
- Example: `www.example.com → 2001:db8::1`

---

## 🔹 3. CNAME Record (Canonical Name / Alias)
- Points one name to another domain name.  
- Example: `mail.example.com → www.example.com`

---

## 🔹 4. MX Record (Mail Exchange)
- Defines mail servers for a domain.  
- Example: `example.com → mail server = mail.example.com`

---

## 🔹 5. PTR Record (Pointer Record)
- Used in **Reverse Lookup Zone**.  
- Maps **IP address → domain name**.  
- Example: `192.168.10.1 → server1.example.com`

---

## 🔹 6. NS Record (Name Server)
- Defines the **authoritative DNS server** for the domain.  
- Example: `example.com → ns1.example.com`

---

## 🔹 7. SOA Record (Start of Authority)
- Stores main information about the zone (Primary server, admin email, version, refresh time).  
- Example: Zone settings for `example.com`.

---

## 🔹 8. SRV Record (Service Record)
- Defines services like **_ldap, _kerberos** used in Active Directory.  
- Example: `_ldap._tcp.dc._msdcs.example.com`

---

## 🔹 9. TXT Record
- Stores text information (often used for **SPF, DKIM, verification**).  
- Example: `v=spf1 include:_spf.google.com ~all`

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

## 📘 DNS Zones Under Reverse Lookup Zone – Primary

- Contains the **master copy** of DNS records (read/write).  
- Acts as the **authoritative source** for its domain namespace.  
- Only one **Primary Zone** exists per DNS namespace.  
- Stores records like **A, CNAME, MX, PTR, SRV** etc.  
- Changes (add, modify, delete records) can be made **only here**.  
- Can replicate data to **Secondary Zones** for redundancy.


## 📘 Secondary Zone  

### 🔹 What is Secondary Zone?  
- A **read-only copy** of the Primary Zone.  
- Updated through **Zone Transfer**.  
- Provides **redundancy + load balancing**.  
- Cannot be edited directly.  

✅ In short: **Backup of Primary Zone (Read-only)**  


# 🔎 DNS Queries: Recursive vs Iterative

When a client asks DNS to resolve a domain, two types of queries happen: **Recursive** and **Iterative**.

---

## 🔹 Recursive Query
- In recursive, the **DNS server does all the work** for the client.  
- The client (e.g., your PC) asks → "Give me the IP of www.microsoft.com".  
- The DNS server then:
  1. Checks its cache.
  2. If not found, it contacts **Root → TLD → Authoritative DNS** servers.
  3. Finally, it returns the **final answer (IP)** to the client.
- ✅ Client gets only one reply (final IP or error).

**Example:**  
Your PC asks **8.8.8.8 (Google DNS)** for `www.microsoft.com`.  
Google DNS finds the answer and returns only the IP to you.

---

## 🔹 Iterative Query
- In iterative, the **DNS server gives the best answer it knows**.  
- If it doesn’t know the exact IP, it replies with a **referral** (next server to ask).  
- Then **your resolver (client-side or local DNS)** goes step by step:
  1. Ask Root → it says "Go to .com servers".
  2. Ask .com → it says "Go to microsoft.com servers".
  3. Finally, ask microsoft.com → it gives IP.

- ✅ Client may contact multiple DNS servers until it gets the final answer.

**Example:**  
Your PC itself goes Root → TLD → Authoritative DNS step by step until it gets IP.

---

## 📌 Key Difference

| Feature              | Recursive Query | Iterative Query |
|-----------------------|-----------------|-----------------|
| Who finds the final IP? | DNS server does | Client/local resolver does |
| Response              | One final answer | Referrals (next server) |
| Speed                 | Faster for client | Slower (client does more work) |
| Usage                 | Most client PCs use this | Between DNS servers |

---
# 📡 DHCP and DORA Process

---

## 🔹 What is DHCP?
- DHCP = **Dynamic Host Configuration Protocol**  
- It **automatically gives IP addresses** and other network settings to clients (PCs, laptops, phones).  
- No need to assign IP manually.  
- It provides:  
  - **IP Address**  
  - **Subnet Mask**  
  - **Default Gateway**  
  - **DNS Server**  

✅ Makes network management easy.

---

## 🔹 DORA Process (How DHCP Works)

When a client joins the network, it follows the **DORA** process:

1. **D → Discover**  
   - Client broadcasts: "Is there any DHCP server? I need an IP!"  

2. **O → Offer**  
   - DHCP server replies: "Yes, I have an IP for you (e.g., 192.168.10.3)."  

3. **R → Request**  
   - Client says: "I want to use this offered IP (192.168.10.3)."  

4. **A → Acknowledge**  
   - DHCP server confirms: "Okay, this IP is yours. You can use it."  

✅ Now client gets full network config and can communicate.

---

## 📌 Example
- Client joins → Gets IP: **192.168.10.3**  
- Subnet Mask: **255.255.255.0**  
- Gateway: **192.168.10.1**  
- DNS: **192.168.10.2**

---

## 📊 Summary

| Step | Name       | Who Sends | Purpose |
|------|------------|-----------|---------|
| D    | Discover   | Client    | "Who can give me IP?" |
| O    | Offer      | Server    | "Here’s an IP you can use." |
| R    | Request    | Client    | "I want this IP." |
| A    | Acknowledge| Server    | "Confirmed, IP is yours." |

✅ In short: **DORA = How DHCP assigns IP automatically.**


# 💽 MBR vs GPT (Disk Partition Styles)

---

## 🔹 What is MBR?
- **MBR = Master Boot Record**  
- Old partition style (introduced in 1983).  
- Stores partition info in the **first sector of the disk**.  
- Supports **only up to 2 TB disks**.  
- Can have **maximum 4 primary partitions**.  
- Used in **BIOS-based systems**.  

✅ Good for old systems, but limited.

---

## 🔹 What is GPT?
- **GPT = GUID Partition Table**  
- Newer standard (replaces MBR).  
- Supports **disks larger than 2 TB**.  
- Can have **128 partitions** (no need for extended partitions).  
- Stores **multiple copies** of partition data → more reliable.  
- Works with **UEFI-based systems**.  

✅ Modern, more secure, supports big storage.

---

## 📊 Key Differences

| Feature            | MBR                        | GPT                         |
|--------------------|----------------------------|-----------------------------|
| Full Form          | Master Boot Record         | GUID Partition Table        |
| Max Disk Size      | 2 TB                       | 9.4 ZB (theoretical)        |
| Max Partitions     | 4 Primary (or 3 + Extended)| 128 Partitions              |
| Compatibility      | Older systems (BIOS)       | Modern systems (UEFI)       |
| Reliability        | Stores single boot data    | Stores multiple copies      |
| Year Introduced    | 1983                       | 2010+ (with UEFI)           |

---
