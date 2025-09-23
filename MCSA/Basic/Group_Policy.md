1. click on on Tool 
2. Click on Active directory User And Computer
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2f1b0073-db2a-43ce-bbbb-4cd7f89d4704" />

## Create ORGANIZATION UNIT HR, RMG, PROJECT 
3. click on right click on microsoft.com
4. click on new
5. click on organization unit
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/60b90eb4-dd38-46c1-9382-b1a1d4a15f38" />
6. type name `HR`
7. click ok
<img width="1905" height="1079" alt="image" src="https://github.com/user-attachments/assets/c8c72ac9-ef48-4c71-9e66-f344b500ec2d" />

Now create HR OU
Same Configuration For RMG AND PROECT
## CREATE USER UNSER ORGANIZATION UNIT  
HR Under - HR1, HR2, HR3
RMG Under- RMG1, RMG2, RMG3
PROJECT UNDER-PROJECT1, PROJECT2,PROJECT3

### CONFIGURATION
1. Right Click on HR
2. click on new
3. click on user
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/05ed8b49-1459-4809-8dda-83f89d1e5a86" />
4. type first name `HR1`
5. Type logon name `HR1`
6. click Next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e74589ae-3f17-49fd-91c3-0658939f972e" />
7. TYPE YOUR PASSWORD
8. TICK ON PASSWORD NEVER EXPIRE
9. CLICK NEXT
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/fd7d4e47-8daa-46a8-afd9-e62d45fda89d" />

SAME CREATE USER HR2 AND HR3 
SAME CONFIGURATION FOR RMG USERS AND PROJECT 
10. NOW YOU SEE ORGANIZATION UNIT AND USERS
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e4c79de7-e0c7-489b-9ea8-cc764060fd90" />

## GROUP POLICY
microsoft.com policy

1. Go to SERVER Manager
2. Click on Tool
3. click on Group Policy Management
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/656f0b47-baf7-475b-b988-1c6f87f688d8" />

1. CLICK ON FOREST: microsoft.com
2. click on domain
3. click on microsoft.com
4. Right click on Defalte domain policy
5. click on Edit
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/ee2f9a9f-3a2c-43a3-a33d-562ebec98adf" />
13. click on user Configuration
14. click on policy
15. click on administrative template
16. click on start mene and start bar
17. select remove run menu from start menu
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7c79b2fb-96eb-4d75-87c5-af609beb622d" />
18. select on anable
19. click on anable
20. click on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/103f5442-a60d-44b5-a9bc-483bfb2c45b0" />

## Verify
1. Go to server2
2. power on the serve 2
3. click on other user
4. type user name `HR1`
5. type Password `Pass@123`
<img width="1919" height="1071" alt="image" src="https://github.com/user-attachments/assets/6fff2f59-8b15-40d4-8f76-c9ef18d69169" />

6. curser moveto window icone
7. click on run
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8a2a7428-c9b9-44e1-acf2-27857e8c7fbb" />
8. now see this eroor
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/0cca57c8-f99c-4b53-bab8-9c9be22f48f1" />


HR Policy 

4. CLICK ON FOREST: microsoft.com
5. click on domain
6. click on microsoft.com
7. right click on HR
8. click create GPO in this domain , and like it here
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/c37ff1f8-7c1a-415f-b30c-f87485e75c01" />

9. type policy name `HRPOLICY`
10. click on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1cdfebea-6984-4cc3-9d12-ac7affb05e73" />

11. Right click on HRPOLICY
12. click on Edit
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d159bf4c-e7b1-4000-9ea2-7d08b3771ead" />
13. click on user Configuration
14. click on policy
15. click on administrative template
16. click on start mene and start bar
17. select remove run menu from start menu
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/351e736e-4eb3-43de-a58f-58a4464de930" />
