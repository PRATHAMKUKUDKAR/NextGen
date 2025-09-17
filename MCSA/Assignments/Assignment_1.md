# Active Directory – User Creation, Folder Sharing & Permissions

---

## Step 1: Create Users in Active Directory
1. Login to **Server1** → Open **Server Manager**.  
2. Go to **Tools → Active Directory Users and Computers**.  
3. In the left panel, right-click on the domain (e.g., `microsoft.com`) → **New → User**.  

![Create User](https://github.com/user-attachments/assets/4095e1b9-5a4d-4b75-ac4d-c93d2ae1f80b)

4. Enter details:  
   - **First Name:** `Pritam`  
   - **User logon name:** `Pritam`  

![User Details](https://github.com/user-attachments/assets/20f85f65-a75a-4cfd-b538-66ab24fef239)

5. Set Password:  
   - Password: `Pass@123`  
   - Confirm Password: `Pass@123`  
   - Tick **Password never expires**  

![Password](https://github.com/user-attachments/assets/7d1a7d0f-b657-4b46-9383-0563ad445af2)

6. Click **Next → Finish**.  

![Finish](https://github.com/user-attachments/assets/2bad4e0a-f46b-4f3b-b43f-44e5b7fd15c5)

👉 Repeat the same steps for users: **Pratik** and **Radha**.  

✅ Now all three users are created.  

![All Users](https://github.com/user-attachments/assets/187a67a8-a56c-4e98-8d72-9c534ff9a144)

---

## Step 2: Create a Folder on Server1
1. Open **File Explorer** → Go to `C:\`.  
2. Right-click → **New → Folder** → Name it `Demo`.  

![Create Folder](https://github.com/user-attachments/assets/854be995-0bf7-4654-b301-53edc19ebb07)

---

## Step 3: Share the Folder
1. Right-click on the `Demo` folder → **Properties**.  
2. Go to the **Sharing** tab → **Advanced Sharing**.  
3. Tick **Share this folder** → Apply → OK.  

![Sharing](https://github.com/user-attachments/assets/330f9026-e3ce-46c4-8e62-df2e5dd82552)

---

## Step 4: Assign Share Permissions

### Add Radha (Full Control)
1. In **Permissions** tab → Click **Add**.  
2. Type `Radha` → Click **Check Names** → OK.  
3. Select **Radha@microsoft.com** → Tick **Full Control → Allow**.  

![Radha Full Control](https://github.com/user-attachments/assets/c61d09ff-6120-44d1-a006-178a1a57bf05)

---

### Add Pritam (Change)
1. Click **Add** → Enter `Pritam`.  
2. Select **Pritam@microsoft.com** → Tick **Change → Allow**.  

![Pritam Change](https://github.com/user-attachments/assets/db680096-7f85-429c-a907-72e78d1c372f)

---

### Add Pratik (Read)
- By default, **Everyone** already has **Read** permission.  
- So Pratik automatically gets **Read access**.  

![Pratik Read](https://github.com/user-attachments/assets/981d6e69-c4c5-418a-9a38-61dad6fae12f)

---

## Step 7: Modify Security Permissions from Server2

1. Login to **Server2** as a user **Pritam**.  
2. Press **Windows + R** → Type `\\Server1` → Press Enter.  
3. Right-click on the shared **Demo** folder → Select **Properties**.  

![Properties](https://github.com/user-attachments/assets/cdd7e5b5-10ce-41a8-8e0c-ad581cd9ff26)

4. Go to the **Security** tab.  
5. Select **Radha (Radha@microsoft.com)** → Click **Edit**.  
6. In the permissions list, **uncheck Full Control**.  
7. Click **Apply → OK**.  

---

## Step 8: Verify Access Denied

- Once Radha’s **Full Control** is removed, she will **no longer have full rights** to the folder.  
- When Radha tries to open or modify the folder, an **Access Denied** message will appear.  

![Access Denied](https://github.com/user-attachments/assets/c47e2468-a6ce-4cf7-8f2a-acf083365a42)

---
