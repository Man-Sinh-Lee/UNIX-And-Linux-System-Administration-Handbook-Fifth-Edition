### Chapter 8: User Management - Summary with Example Commands

---

#### **8.1 Account Mechanics**
- Users are identified by their **User ID (UID)**, a 32-bit integer.
- APIs such as `getpwuid()` and `getpwnam()` map UIDs to user details like names and home directories.
- `/etc/passwd` stores primary user details, with external sources like LDAP extending this functionality.

---

#### **8.2 The `/etc/passwd` File**
- Holds seven fields:
  1. **Login name** (unique, max 32 characters).
  2. **Encrypted password placeholder** (`x` for shadow passwords in Linux).
  3. **UID**.
  4. **Default Group ID (GID)**.
  5. **GECOS field**: Optional personal info.
  6. **Home directory**.
  7. **Login shell**.

Example:
```bash
# View entries
cat /etc/passwd
```

---

#### **8.3 The Linux `/etc/shadow` File**
- Stores encrypted passwords and additional account settings, e.g., password aging.
- Contains nine fields, such as the **last password change date** and **expiration date**.

Example:
```bash
# Check shadow file entries
sudo cat /etc/shadow
```

---

#### **8.4 FreeBSD’s `/etc/master.passwd` and `/etc/login.conf`**
- **/etc/master.passwd**:
  - Stores sensitive user data, including encrypted passwords.
  - Use `vipw` to edit safely.

Example:
```bash
# Edit master.passwd
sudo vipw
```

- **/etc/login.conf**:
  - Controls login classes, resource limits, environment variables, etc.

---

#### **8.5 The `/etc/group` File**
- Defines UNIX groups, linking users and permissions.
- Fields include **group name**, **password placeholder**, **GID**, and **members**.

Example:
```bash
# Add a group
sudo groupadd developers
```

---

#### **8.6 Manual Steps for Adding Users**
1. Add user to `/etc/passwd` and `/etc/group`.
2. Set a password using `passwd`.
3. Create and configure the home directory.
4. Assign startup files (e.g., from `/etc/skel`).

Example:
```bash
# Create a home directory
mkdir /home/username
chown username:username /home/username
```

---

#### **8.7 Scripts for Adding Users**
- Tools like `useradd`, `adduser`, and `newusers` simplify user management.
- **useradd**:
  ```bash
  sudo useradd -m -s /bin/bash -G sudo username
  ```
- **adduser** (interactive):
  ```bash
  sudo adduser username
  ```

---

#### **8.8 Safe Removal of a User’s Account and Files**
1. Lock the account.
2. Archive and optionally delete the home directory.
3. Remove user entries from `/etc/passwd` and `/etc/group`.

Example:
```bash
# Remove a user and archive home
sudo userdel -r username
```

---

#### **8.9 User Login Lockout**
- Temporarily lock accounts using `passwd`:
  ```bash
  sudo passwd -l username
  ```
- Permanently disable accounts by setting invalid shells.

---

#### **8.10 Risk Reduction with PAM**
- PAM modules enforce security policies like:
  - Password strength checks.
  - Login attempt limits.

Example:
```bash
# Edit PAM password policy
sudo nano /etc/pam.d/common-password
```

---

#### **8.11 Centralized Account Management**
- Use LDAP or Active Directory for consistent UID/GID mapping and account management across systems.

Example:
```bash
# Query LDAP user details
ldapsearch -x -b "dc=example,dc=com" "(uid=username)"
```

---

This summary includes practical examples and commands for user management. Let me know if you need further elaboration on any section!