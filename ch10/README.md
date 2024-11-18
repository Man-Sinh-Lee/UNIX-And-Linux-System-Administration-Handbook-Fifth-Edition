### Chapter 10: Logging - Summary with Example Commands

#### **10.1 Log Locations**
- **Default Location**: Most log files are stored under `/var/log/`.
- **Examples**:
  - `/var/log/syslog` (general system messages).
  - `/var/log/auth.log` (authentication-related events).
- Some applications (e.g., databases) use their own log locations.
- Logs can grow rapidly; use separate partitions for `/var/log` to prevent disk issues.

Example:
```bash
# View the last 10 lines of syslog
tail -n 10 /var/log/syslog
```

---

#### **10.2 The Systemd Journal**
- **Binary Logs**: Unlike plain text syslog, systemd journal stores logs in an indexed binary format.
- **Advantages**:
  - Faster searches.
  - Persistent or volatile storage configurable via `/etc/systemd/journald.conf`.
- **Commands**:
  ```bash
  # View all logs
  journalctl

  # Follow real-time logs
  journalctl -f

  # Logs for a specific unit
  journalctl -u sshd
  ```

---

#### **10.3 Syslog**
- **Description**: An older, widely-used system for logging (via `rsyslog`).
- **Key Features**:
  - Facilities: Group logs by type (e.g., `auth`, `cron`).
  - Severities: Filter logs by importance (`emerg`, `crit`, `info`).
- **Configuration**:
  - Configured in `/etc/rsyslog.conf`.
  - Example to log authentication messages:
    ```bash
    auth.* /var/log/auth.log
    ```
- Restart the service after changes:
  ```bash
  sudo systemctl restart rsyslog
  ```

---

#### **10.4 Kernel and Boot-Time Logging**
- **Kernel Logs**:
  - Accessed via `journalctl -k` or `dmesg`.
- **Boot Logs**:
  ```bash
  # Show logs for the last boot
  journalctl -b

  # Display boot-time messages
  dmesg | less
  ```
- **Managing Console Logging**:
  - Adjust verbosity using `dmesg`:
    ```bash
    dmesg -n 4  # Only errors and critical messages
    ```

---

#### **10.5 Management and Rotation of Log Files**
- **Tools**:
  - **logrotate** (Linux):
    - Configurations in `/etc/logrotate.conf` and `/etc/logrotate.d/`.
    - Example for weekly rotation:
      ```bash
      /var/log/messages {
          weekly
          rotate 4
          compress
          missingok
          notifempty
      }
      ```
  - **newsyslog** (FreeBSD):
    - Configured in `/etc/newsyslog.conf`.
- **Best Practices**:
  - Delay compression for active logs using `delaycompress`.

Example:
```bash
# Test logrotate configuration
logrotate -d /etc/logrotate.conf
```

---

#### **10.6 Management of Logs at Scale**
- **Centralized Logging**:
  - Tools like the **ELK stack** (Elasticsearch, Logstash, Kibana) or **Graylog**.
- **Advantages**:
  - Easier searches across distributed systems.
  - Better visualization and alerting.

Example:
```bash
# Use Filebeat to send logs to an ELK server
sudo filebeat setup
sudo filebeat -e
```

---

#### **10.7 Logging Policies**
- **Retention Policies**:
  - Define how long logs are stored.
  - Align with compliance requirements (e.g., PCI DSS, ISO 27001).
- **Best Practices**:
  - Ensure secure storage.
  - Use timestamps validated via NTP.
  - Regularly review logs for anomalies.

Example Policy Configuration:
```bash
# Log retention in logrotate.conf
/var/log/secure {
    monthly
    rotate 12
    missingok
    compress
}
```

---

This summary includes practical examples and commands for managing logs. Let me know if you need more details on specific sections!