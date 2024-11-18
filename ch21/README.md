### Chapter 21: The Network File System (NFS) - Summary with Examples

---

#### **21.1 Meet Network File Services**
- **Purpose**: Share files and directories across systems, maintaining a seamless user experience as if files were local.
- **Competition**:
  - **NFS**: Common in UNIX/Linux environments.
  - **SMB (via Samba)**: Preferred for hybrid environments with Windows.
- **Challenges**: Includes edge cases in security, performance, and reliability.

---

#### **21.2 The NFS Approach**
- **History**:
  - NFS was introduced in 1984 by Sun Microsystems.
  - Evolved with three versions: V2 (1989), V3 (early 1990s), and V4 (2003 onwards).
- **Advantages**:
  - Platform independence.
  - Strong modular security (with V4).
  - Support for replication, migration, and Unicode filenames.
- **Protocol Versions**:
  - Use V4 where possible; it integrates features like locking and mount protocols.

---

#### **21.3 Server-Side NFS**
- **Exporting Directories**:
  - Use `/etc/exports` to specify exported directories and their permissions.
  - Activate changes:
    ```bash
    # Linux
    sudo exportfs -a
    # FreeBSD
    sudo service nfsd restart
    ```
- **Daemon Management**:
  - **Linux**: Use `nfsd` and `exportfs`.
  - **FreeBSD**: Use `mountd` and `nfsd`.
  ```bash
  # Start NFS service
  sudo systemctl start nfs-server
  ```

---

#### **21.4 Client-Side NFS**
- **Mounting Filesystems**:
  ```bash
  # Mount a remote NFS share
  sudo mount -t nfs server:/exported/directory /mnt
  ```
- **Persistent Mounts**: Add entries in `/etc/fstab` for automatic mounts at boot.
- **Troubleshooting**:
  - Verify server exports:
    ```bash
    showmount -e server
    ```

---

#### **21.5 Identity Mapping for NFS Version 4**
- **Purpose**: Map user and group IDs between clients and servers.
- **Configuration**:
  - Ensure consistent NFS domains across systems.
  - Restart mapping daemons after updates:
    ```bash
    # Example on Linux
    sudo systemctl restart nfs-idmapd
    ```

---

#### **21.6 NFSSTAT: Dump NFS Statistics**
- **Tool**: Analyze server and client-side performance.
  ```bash
  # Show NFS statistics
  nfsstat -s   # Server-side stats
  nfsstat -c   # Client-side stats
  ```

---

#### **21.7 Dedicated NFS File Servers**
- Benefits include:
  - Optimized NFS performance.
  - Scalable storage for large deployments.
  - Reliable hardware with integrated features like mirroring and security.

---

#### **21.8 Automatic Mounting**
- **Autofs**:
  - Automatically mount filesystems when accessed.
  ```bash
  # Restart autofs on changes
  sudo systemctl reload autofs
  ```

---

#### **21.9 Recommended Reading**
- Refer to NFS RFCs for detailed protocol specifications:
  - RFC 1094, 1813, and 7530 for V2, V3, and V4 respectively.

This detailed summary includes examples for configuring and managing NFS systems. Let me know if you need further assistance!