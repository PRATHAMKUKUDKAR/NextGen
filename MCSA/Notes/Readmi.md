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
