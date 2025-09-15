# 🖥️ Active Directory – Create and Verify User & Group  

This guide explains how to **create and verify a user in Active Directory (AD)** and also how to **create a group** in Windows Server.  

---

## 📌 Part 1: Create and Verify User in Active Directory (Server1)  

### Step 1: Open Server Manager  
1. Login to **Server1**.  
2. Click on the **Windows Start Button**.  
3. Select **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/afa33e0b-2de1-4bca-93cc-b4f173cf2eaa)

---

### Step 2: Open Active Directory Users and Computers  
1. In **Server Manager**, click on **Tools** (top-right).  
2. Select **Active Directory Users and Computers**.  

![ADUC](https://github.com/user-attachments/assets/cffbdf61-0e8e-4697-b55e-78b7b89e302c)

---

### Step 3: Create a New User  
1. In the left panel, right-click on your domain name (e.g., `microsoft.com`).  
2. Select **New → User**.  

![New User](https://github.com/user-attachments/assets/b5eab2f5-f2a5-455a-b47a-f98353e92e0f)

---

### Step 4: Enter User Details  
1. Enter the **Full Name** → `Demo`  
2. Enter the **User logon name** → `Demo`  
3. Click **Next**.  

![User Details](https://github.com/user-attachments/assets/ce23dbbc-a4ed-48bc-9849-8f858bc9a54f)

---

### Step 5: Set User Password  
1. Enter a password → Example: `xyz`.  
2. Select the option: **User must change password at next logon**.  
   - This ensures the user sets a new password on first login.  
3. Click **Next**.  

![Password](https://github.com/user-attachments/assets/eb7ca83b-f790-480b-896c-cb84cd4cb309)

---

### Step 6: Finish User Creation  
1. Click **Finish** to complete the process.  

![Finish User](https://github.com/user-attachments/assets/b042c91c-81ee-47ed-a169-77fd3acbe504)

---

### ✅ Result  
- The new user **Demo** has been successfully created under the domain.  

![User Created](https://github.com/user-attachments/assets/0f2523a3-6670-455c-a496-409ee2eec059)

---

## 📌 Part 2: Verify User Login on Server2  

### Step 1: Open Server2 Login Screen  
1. On **Server2**, click on **Other User**.  

![Other User](https://github.com/user-attachments/assets/dd276b07-08e1-4eb9-bd16-cc07d0526d6d)

---

### Step 2: Enter User Credentials  
1. Type the **Username** → `Demo`  
2. Type the **Password** → `xyz`  

![Login](https://github.com/user-attachments/assets/6bcd55aa-fe73-4aee-94d7-8d4c3f0f882c)

---

### Step 3: Force Password Change  
- A pop-up will appear → **The user must change password before logging in**.  
- Click **OK**.  

![Force Password Change](https://github.com/user-attachments/assets/87aacb07-06f8-4af1-b3a8-ca447391121d)

---

### Step 4: Set a New Password  
1. Enter a **new password**.  
2. Confirm the password.  
3. Click **OK**.  

![New Password](https://github.com/user-attachments/assets/8143aff4-cec9-4083-a926-fa86bf07885e)

---

### ✅ Final Result  
- User **Demo** is successfully logged into **Server2** with the new password. 🎉  

---

## 📌 Part 3: Create a Group in Active Directory  

### Step 1: Open Server Manager  
1. Login to **Server1**.  
2. Click on the **Windows Start Button**.  
3. Select **Server Manager**.  

![Server Manager](https://github.com/user-attachments/assets/afa33e0b-2de1-4bca-93cc-b4f173cf2eaa)

---

### Step 2: Open Active Directory Users and Computers  
1. In **Server Manager**, click on **Tools** (top-right).  
2. Select **Active Directory Users and Computers**.  

![ADUC](https://github.com/user-attachments/assets/cffbdf61-0e8e-4697-b55e-78b7b89e302c)

---

### Step 3: Create a New Group  
1. In the left panel, right-click on your domain name (e.g., `microsoft.com`).  
2. Select **New → Group**.  

![New Group](https://github.com/user-attachments/assets/ffc5df73-1a8d-4606-a127-741d4edf9216)

3. Type the **Group Name** → `NextGen`.  
4. Select:  
   - **Group Scope** → Global  
   - **Group Type** → Security  
5. Click **OK**.  

![Group Properties](https://github.com/user-attachments/assets/96c91f7c-29ea-4296-b0ae-822bbcfbcf4a)

---

### ✅ Result  
- The new group **NextGen** has been successfully created under the domain.  

![Group Created](https://github.com/user-attachments/assets/65d52bd9-9fbb-48fe-a345-ff13b06dab60)


