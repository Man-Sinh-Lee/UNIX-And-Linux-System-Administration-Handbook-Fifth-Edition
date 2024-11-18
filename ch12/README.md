### Chapter 12: Printing - Summary with Example Commands

---

#### **12.1 CUPS Printing**
- **Overview**:
  - CUPS (Common UNIX Printing System) is the default printing system for Linux, FreeBSD, and macOS.
  - Includes backward-compatible commands like `lp` and `lpr` from legacy systems.
- **Functionality**:
  - CUPS servers use HTTP/IPP for communication.
  - Provides web-based management (`http://localhost:631`).
- **Command Examples**:
  ```bash
  # Print a file to the default printer
  lpr file.pdf
  # View print queue
  lpq
  ```

---

#### **12.2 CUPS Server Administration**
- **Configuration**:
  - Managed through `/etc/cups/cupsd.conf` or the web GUI.
  - Restart required after editing the config file:
    ```bash
    sudo systemctl restart cups
    ```
- **Network Print Server Setup**:
  - Enable remote printing by adjusting `Listen` and `BrowseAddress` settings in `cupsd.conf`.
  ```bash
  Listen 192.168.1.1:631
  BrowseAddress 192.168.1.255:631
  ```
- **Printer Auto-configuration**:
  - Automatically detects USB printers.
  - Network printers require static or DHCP-assigned IP addresses.

---

#### **12.3 Troubleshooting Tips**
- **Restarting the Print Daemon**:
  ```bash
  sudo systemctl restart cups
  ```
- **Log Files**:
  - Located in `/var/log/cups/` (e.g., `error_log`, `page_log`).
- **Direct Printing Connection**:
  - Use the backend tool to check the physical connection:
    ```bash
    lpinfo -v
    ```
- **Network Printing Issues**:
  - Verify name resolution and permissions.
  - Debug using browser access (`hostname:631`) or `telnet`.

---

#### **12.4 Recommended Reading**
- Additional resources include official CUPS documentation and tutorials on network printer configuration and troubleshooting.

This detailed summary includes examples for managing and troubleshooting CUPS-based printing systems. Let me know if you need further clarification!