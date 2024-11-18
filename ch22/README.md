### Chapter 22: SMB - Summary with Example Commands

#### **22.1 Samba: SMB Server for UNIX**
- **Overview**: Samba provides SMB protocol implementation for UNIX/Linux systems, enabling file and printer sharing with Windows clients.
- **Core Components**:
  - `smbd`: Manages file, print, and authentication services.
  - `nmbd`: Handles name resolution and service announcements.
- **Use Cases**:
  - File sharing between UNIX and Windows.
  - Active Directory (AD) integration for authentication.

---

#### **22.2 Installing and Configuring Samba**
- **Installation**:
  - Install Samba on FreeBSD with:
    ```bash
    pkg install samba44
    ```
  - For Linux, use your package manager:
    ```bash
    sudo apt install samba
    ```
- **Configuration File**:
  - Located at `/etc/samba/smb.conf` (Linux) or `/usr/local/etc/smb4.conf` (FreeBSD).
  - Example minimal configuration:
    ```ini
    [global]
    workgroup = WORKGROUP
    security = user
    [share]
    path = /srv/samba/share
    read only = no
    ```
- **Test Configuration**:
  ```bash
  testparm
  ```

---

#### **22.3 Mounting SMB File Shares**
- **Linux Command**:
  ```bash
  sudo mount -t cifs //server/share /mnt -o username=user,password=pass
  ```
- **FreeBSD Command**:
  ```bash
  mount_smbfs //user@server/share /mnt
  ```
- **Options**:
  - Use `uid`, `gid`, `fmask`, and `dmask` to fine-tune permissions.

---

#### **22.4 Browsing SMB File Shares**
- Use `smbclient` to list or interact with shares:
  ```bash
  # List available shares
  smbclient -L //server -U user
  
  # Connect to a share
  smbclient //server/share -U user
  ```

---

#### **22.5 Ensuring Samba Security**
- **Restrict Access**:
  - Use `hosts allow` and `hosts deny` directives in `smb.conf`.
  - Example:
    ```ini
    hosts allow = 192.168.1.0/24
    hosts deny = ALL
    ```
- **Firewall Rules**:
  - Samba uses UDP ports 137-139 and TCP ports 139, 445. Block external access to secure the network.

---

#### **22.6 Debugging Samba**
- **Active Connections**:
  ```bash
  smbstatus
  ```
- **Logging**:
  - Configure logging levels in `smb.conf`:
    ```ini
    log level = 3
    log file = /var/log/samba/log.%m
    ```
  - Adjust debug levels dynamically:
    ```bash
    smbcontrol all debug 4
    ```

---

#### **22.7 Recommended Reading**
- Refer to Red Hat's File and Print Servers guide and the [Samba Wiki](https://wiki.samba.org/) for in-depth guidance.

This summary provides practical examples for setting up, using, and troubleshooting Samba for SMB-based file sharing. Let me know if further details are needed!