

### Step 1: Open Server Manager
1. Click on **Windows Start Button**.  
2. Select **Server Manager**.  

 ![Server Manager](https://github.com/user-attachments/assets/9ee5bcb0-b63f-4496-9185-c603ecd225bc)  

 ### Step 1: Open DHCP Management
1. Go to **Server Manager → Tools → DNS**.  

Forwrd Look Up Zone 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b1c95699-4dd5-4902-96a0-37c9b49600bb" />

# DNS Zones: Forward Lookup & Reverse Lookup

## 🌐 Forward Lookup Zone
- Maps **Domain Name → IP Address**.  
- Most common DNS zone used on the internet.  
- Record types used:  
  - **A Record** → Maps domain name to IPv4 address.  
  - **AAAA Record** → Maps domain name to IPv6 address.  
  - **CNAME Record** → Alias of another domain name.  
  - **MX Record** → Mail exchange server record.  
- Essential for browsing websites, accessing services, and resolving domain names.  
- Example:  
  - `www.nextgen.com` → `192.168.10.1`  

✅ In short: **Forward Lookup Zone = Domain Name → IP Address**

---

## 🔄 Reverse Lookup Zone
- Maps **IP Address → Domain Name**.  
- Performs the reverse function of forward lookup.  
- Record type used:  
  - **PTR Record (Pointer Record)** → Maps IP address back to hostname.  
- Helps in:  
  - **Network troubleshooting** (ping, nslookup, traceroute).  
  - **Email server verification** (anti-spam reverse DNS checks).  
  - **Security auditing** (verify IP belongs to valid domain).  
- Not mandatory, but highly recommended for proper verification.  
- Example:  
  - `192.168.10.1` → `www.nextgen.com`  

✅ In short: **Reverse Lookup Zone = IP Address → Domain Name**

1. Right click on Reverse look up zone
2. click new zone
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/ac760ae0-b431-4384-afd9-8d52f79fef2d" />
 3. click on next
<img width="1919" height="1068" alt="image" src="https://github.com/user-attachments/assets/a2c22c55-5b37-49d4-bd5f-54b969d104aa" />
4. Tick on Primary Zone 
5. click On next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1d47d2ef-d372-4b4f-bae6-56565e5649d6" />

# 📘 DNS Zones Under Reverse Lookup Zone – Primary & Secondary

## 🛠️ Primary Zone
- Contains the **master copy** of DNS records (read/write).  
- Acts as the **authoritative source** for its domain namespace.  
- Only one **Primary Zone** exists per DNS namespace.  
- Stores records like **A, CNAME, MX, PTR, SRV** etc.  
- Changes (add, modify, delete records) can be made **only here**.  
- Zone file is saved locally on the DNS server (e.g., `domain.com.dns`).  
- Can replicate data to **Secondary Zones** for redundancy.

Reverse Lookup Zone name
1. tick ipv4 realise lokup zone
2. click on next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/fd819836-361b-4d09-a0f9-41c4060b3bbc" />

