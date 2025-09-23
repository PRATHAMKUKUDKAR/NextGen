# 🛠️ Active Directory – OU, Users & Group Policy Configuration

This guide explains step-by-step how to **create Organizational Units (OUs)**, **add users**, and **apply Group Policies** in **Active Directory** with screenshots.

---

## 📌 Step 1: Open Active Directory Users and Computers
1. Click on **Tools** in Server Manager.  
2. Select **Active Directory Users and Computers**.  

![Active Directory](https://github.com/user-attachments/assets/2f1b0073-db2a-43ce-bbbb-4cd7f89d4704)

---

## 📌 Step 2: Create Organization Units (OUs)
We will create **HR**, **RMG**, and **PROJECT** OUs.

1. Right-click on `microsoft.com`.  
2. Click on **New → Organizational Unit**.  

![New OU](https://github.com/user-attachments/assets/60b90eb4-dd38-46c1-9382-b1a1d4a15f38)

3. Type name `HR` → Click **OK**.  

![HR OU](https://github.com/user-attachments/assets/c8c72ac9-ef48-4c71-9e66-f344b500ec2d)

➡️ Repeat same steps to create **RMG** and **PROJECT** OUs.

---

## 📌 Step 3: Create Users Under OUs
Example: Creating user **HR1** under **HR OU**.

1. Right-click on **HR OU** → **New → User**.  

![New User](https://github.com/user-attachments/assets/05ed8b49-1459-4809-8dda-83f89d1e5a86)

2. Enter details:  
   - First Name: `HR1`  
   - Logon Name: `HR1`  

![HR1 User](https://github.com/user-attachments/assets/e74589ae-3f17-49fd-91c3-0658939f972e)

3. Set password:  
   - Type password: `Pass@123`  
   - Tick **Password Never Expires** → Click **Next**  

![Password](https://github.com/user-attachments/assets/fd7d4e47-8daa-46a8-afd9-e62d45fda89d)

➡️ Repeat same steps for **HR2, HR3**.  
➡️ Do same for **RMG1, RMG2, RMG3** and **PROJECT1, PROJECT2, PROJECT3**.  

Now your OU and Users will look like this:  

![OU Users](https://github.com/user-attachments/assets/e4c79de7-e0c7-489b-9ea8-cc764060fd90)

---

## 📌 Step 4: Apply Group Policy at Domain Level
Example: **Remove Run option from Start Menu** for all users.

1. Open **Group Policy Management**.  

![GPO](https://github.com/user-attachments/assets/656f0b47-baf7-475b-b988-1c6f87f688d8)

2. Expand → `Forest: microsoft.com → Domains → microsoft.com`.  
3. Right-click on **Default Domain Policy** → Click **Edit**.  

![Edit GPO](https://github.com/user-attachments/assets/ee2f9a9f-3a2c-43a3-a33d-562ebec98adf)

4. Navigate:  
   - **User Configuration → Policies → Administrative Templates → Start Menu and Taskbar**.  
   - Select **Remove Run menu from Start Menu**.  

![Run Menu](https://github.com/user-attachments/assets/7c79b2fb-96eb-4d75-87c5-af609beb622d)

5. Enable Policy → Click **Apply → OK**.  

![Enable Policy](https://github.com/user-attachments/assets/103f5442-a60d-44b5-a9bc-483bfb2c45b0)

---

## 📌 Step 5: Verify Group Policy on Client
1. Log in to **Server2** with user **HR1**.  
   - Username: `HR1`  
   - Password: `Pass@123`  

![Login](https://github.com/user-attachments/assets/6fff2f59-8b15-40d4-8f76-c9ef18d69169)

2. Try opening **Run (Win + R)**.  

![Run](https://github.com/user-attachments/assets/8a2a7428-c9b9-44e1-acf2-27857e8c7fbb)

3. You will get an error (Run is disabled).  

![Error](https://github.com/user-attachments/assets/0cca57c8-f99c-4b53-bab8-9c9be22f48f1)

---

## 📌 Step 6: Apply OU-Level Policy (HR Specific)
1. In **Group Policy Management** → Right-click on **HR OU**.  
2. Select **Create a GPO in this domain, and Link it here**.  

![New GPO](https://github.com/user-attachments/assets/c37ff1f8-7c1a-415f-b30c-f87485e75c01)

3. Name it: `HRPOLICY` → Click OK.  

![HR Policy](https://github.com/user-attachments/assets/1cdfebea-6984-4cc3-9d12-ac7affb05e73)

4. Right-click on `HRPOLICY` → Click **Edit**.  

![Edit HR Policy](https://github.com/user-attachments/assets/d159bf4c-e7b1-4000-9ea2-7d08b3771ead)

5. Navigate same path:  
   - **User Configuration → Policies → Administrative Templates → Start Menu and Taskbar**.  
   - Set **Remove Run menu from Start Menu → Disable**.  

![Disable Policy](https://github.com/user-attachments/assets/970b3ef4-8e1b-46ad-9b86-a00991744b66)

6. Apply → OK.  

![Disable Apply](https://github.com/user-attachments/assets/645b54ab-7039-405b-8d66-e44836567680)

---

## 📌 Step 7: Verify OU Policy
### HR User 
1. Log in to **Server2** with `HR1`.  
2. If policy not applied, run:  

```
gpupdate /force
```
<img width="1919" height="1004" alt="Screenshot 2025-09-23 172503" src="https://github.com/user-attachments/assets/e5db63e4-7f11-4fb1-a3dc-43bd1b7c7f82" />

3. Go to Window icon
4. click on right click
5. clik on run
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/11ec8aca-2b35-4b21-8eec-c67b57db0f3e" />

> ✅ This works because the policy has been applied to the HR user.


### Rmg User

1. On **Server2** log in as `RMG1 / Pass@123`.  
   ![RMG1 login](https://github.com/user-attachments/assets/09842651-f293-4059-ae1d-aae508fde26f)

2. Try open **Run** (Win + R) — nothing happens / error shown.  
   ![Open Run](https://github.com/user-attachments/assets/8a2a7428-c9b9-44e1-acf2-27857e8c7fbb)  

3. Error message when attempting Run:  
   ![Run error](https://github.com/user-attachments/assets/0cca57c8-f99c-4b53-bab8-9c9be22f48f1)

> ❌ This does not work because the policy has not been applied to the RMG user.
---

