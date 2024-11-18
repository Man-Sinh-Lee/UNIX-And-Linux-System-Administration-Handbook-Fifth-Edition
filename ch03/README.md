### Chapter 3: Access Control and Rootly Powers - Detailed Summary with Example Codes

#### **3.1 Standard UNIX Access Control**
- **Principles**:
  - Files and processes are owned by users and groups.
  - Access is managed using **read (r)**, **write (w)**, and **execute (x)** permissions.
  - The superuser (`root`) has unrestricted access.

- **File Access Example**:
  ```bash
  ls -l file.txt
  # Output: -rw-r--r-- 1 user group 1234 Oct 18 12:00 file.txt
  chmod 750 file.txt
  ls -l file.txt
  # Output: -rwxr-x--- 1 user group 1234 Oct 18 12:00 file.txt
  ```

- **Process Ownership**:
  Each process is associated with a UID and GID. Privileged operations require the user to own the process or be `root`.

---

#### **3.2 Management of the Root Account**
- **Root Account Characteristics**:
  - Superuser privileges allow full system control.
  - Direct login to the root account is often discouraged for security reasons.
  - Tools like `su` and `sudo` enable controlled privilege escalation.

- **Using `su`**:
  ```bash
  su -
  # Switch to root after entering the root password.
  ```

- **Using `sudo`**:
  ```bash
  sudo apt update
  # Execute commands with elevated privileges without switching to the root account.
  ```

- **Disabling Root Login**:
  - Root login can be disabled by locking the account:
    ```bash
    sudo passwd -l root
    ```

---

#### **3.3 Extensions to the Standard Access Control Model**
- **Pluggable Authentication Modules (PAM)**:
  - Modular framework for authentication.
  - Example PAM configuration for SSH:
    ```bash
    cat /etc/pam.d/sshd
    auth required pam_unix.so
    ```

- **Filesystem Access Control Lists (ACLs)**:
  - Provide granular permissions.
  ```bash
  setfacl -m u:john:rwx file.txt
  getfacl file.txt
  ```

- **Linux Capabilities**:
  - Break down root privileges into discrete units, such as binding privileged ports.
  ```bash
  # Assign capability to bind privileged ports.
  sudo setcap CAP_NET_BIND_SERVICE=+ep /usr/bin/my_app
  ```

---

#### **3.4 Modern Access Control**
- **Mandatory Access Control (MAC)**:
  - Enforce strict access policies using frameworks like SELinux or AppArmor.
  - Example SELinux command:
    ```bash
    getenforce
    # Check SELinux mode.
    setenforce 1
    # Set to enforcing mode.
    ```

- **Role-Based Access Control (RBAC)**:
  - Assign permissions to roles, then link roles to users.

---

#### **3.5 Recommended Reading**
- Suggested topics for further exploration:
  - PAM modules and configuration.
  - SELinux and AppArmor policies.
  - Filesystem ACLs and practical use cases.
  - Advanced tools like `sudo` and their configurations.

This summary includes practical examples to demonstrate the topics discussed. If you need more detailed examples or explanations, let me know!