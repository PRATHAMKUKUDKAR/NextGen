# Router Configuration Modes (Enable, Config T)

## 🔹 Explanation of Modes

- **User EXEC mode (`Router>`):**
  - Default mode after boot/login.
  - Limited access (basic monitoring).
  - Can use simple commands like `ping`, `show version`.

- **Privileged EXEC mode (`Router#`):**
  - Accessed by typing `enable`.
  - Provides more commands (view configs, debug, backups).
  - Needed before making any configuration changes.

- **Global Configuration mode (`Router(config)#`):**
  - Entered using `configure terminal` from Privileged EXEC.
  - Used for device-wide settings (hostname, passwords, routing protocols).

---
# Router Configuration Modes in Cisco Packet Tracer

## Step 1: Open Router
- Open **Cisco Packet Tracer**.
- Drag and drop a **Router** into the workspace.
- Click on the router → go to **CLI tab**.
- You will see:
  ```bash
  Router>
  ```
  <img width="600" height="536" alt="Screenshot 2025-09-01 223355" src="https://github.com/user-attachments/assets/93d540ff-f31e-4f00-8424-3db5ae022588" />

## Step 2: Privileged EXEC Mode
```bash
Router> enable
Router#
```
<img width="478" height="117" alt="Screenshot 2025-09-01 223525" src="https://github.com/user-attachments/assets/1c599ddc-d5f0-4c64-ab2b-da9697bf977e" />

## Step 3: Global Configuration Mode
```bash
Router# configure terminal
Router(config)#
```
<img width="705" height="254" alt="Screenshot 2025-09-01 223615" src="https://github.com/user-attachments/assets/87f2e659-4f1e-40f2-9f2c-668aa1fdfa27" />
