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

## 🔹 Steps to Enter Modes (CLI)

1. **Start in User EXEC mode**
   ```bash
   Router>              # User EXEC
