### Chapter 5: The Filesystem - Detailed Summary with Example Codes

#### **5.1 Pathnames**
- **Unified Hierarchy**: The filesystem starts at the root directory (`/`) and includes all subdirectories and files.
- **Absolute vs. Relative Pathnames**:
  - **Absolute**: Start with `/` (e.g., `/usr/local/bin`).
  - **Relative**: Start from the current directory (e.g., `docs/reports`).

Example:
```bash
# Display absolute and relative paths
pwd           # Prints the absolute path of the current directory
ls ../folder  # Relative path usage to list files in a parent directory
```

---

#### **5.2 Filesystem Mounting and Unmounting**
- **Mount Command**: Attaches filesystems to the directory tree.
- **Unmount Command**: Detaches filesystems.
- **Configuring Mounts**:
  - **Manual Mounting**:
    ```bash
    mount /dev/sda1 /mnt
    ```
  - **Using `/etc/fstab`** for persistent configurations.

Example:
```bash
# Display all mounted filesystems
mount
# Add an entry to /etc/fstab for auto-mounting
echo "/dev/sda1 /mnt ext4 defaults 0 2" >> /etc/fstab
```

---

#### **5.3 Organization of the File Tree**
- **Standard Directories**:
  - **Root (`/`)**: Contains essential system files.
  - **/etc**: Configuration files.
  - **/usr**: User utilities and applications.
  - **/var**: Logs and spool directories.
- **Partitioning**: Often used to manage space and prevent a single directory from filling up the disk.

Example:
```bash
# Inspect the filesystem hierarchy
ls /
```

---

#### **5.4 File Types**
- **Regular Files**: Text or binary data.
- **Directories**: Containers for files.
- **Symbolic Links**: Pointers to other files or directories.
- **Device Files**: Represent hardware devices.
- **Sockets and Pipes**: Enable inter-process communication.

Example:
```bash
# Create a symbolic link
ln -s /original/file /link/to/file
```

---

#### **5.5 File Attributes**
- **Permission Bits**: Determine read (`r`), write (`w`), and execute (`x`) access for user (`u`), group (`g`), and others (`o`).
- **Special Bits**:
  - **Setuid/Setgid**: Execute a program with the file owner's permissions.
  - **Sticky Bit**: Restricts deletion to the file owner.

Example:
```bash
# Set sticky bit on a directory
chmod +t /shared/directory
```

---

#### **5.6 Access Control Lists (ACLs)**
- **Purpose**: Provide fine-grained control beyond traditional permissions.
- **Commands**:
  - `setfacl`: Set ACL permissions.
  - `getfacl`: Display ACL permissions.

Example:
```bash
# Grant specific user rwx access
setfacl -m u:username:rwx file.txt
# View ACL settings
getfacl file.txt
```

---

Let me know if you'd like additional examples or explanations for any section!