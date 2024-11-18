### Chapter 20: Storage - Summary with Examples

---

#### **20.1 I Just Want to Add a Disk!**
- **Scenario**: Adding a new disk without advanced configurations like RAID.
- **Steps**:
  - **Attach the disk**: Either physically (e.g., SATA, USB) or virtually (cloud environments).
  - **Identify the disk**:
    ```bash
    # List disks on Linux
    lsblk
    ```
  - **Partition and format**:
    ```bash
    # Create a partition
    fdisk /dev/sdX
    # Format the partition
    mkfs.ext4 /dev/sdX1
    ```
  - **Mount the disk**:
    ```bash
    mkdir /mnt/newdisk
    mount /dev/sdX1 /mnt/newdisk
    ```

---

#### **20.2 Storage Hardware**
- **Types**:
  - Hard Disk Drives (HDDs): High capacity, slower.
  - Solid-State Drives (SSDs): High performance, lower latency.
  - Hybrid Drives: Combine HDDs with flash storage for caching.
- **Use Cases**:
  - SSDs for performance-sensitive tasks.
  - HDDs for archival or bulk storage.

---

#### **20.3 Storage Hardware Interfaces**
- **Common Interfaces**:
  - **SATA**: Most prevalent; supports hot-swapping.
  - **SAS**: High-performance alternative to SATA.
  - **USB**: For external storage.
  - **PCIe**: High-speed interface for NVMe SSDs.

---

#### **20.4 Attachment and Low-Level Management of Drives**
- **Tools**:
  - `smartctl`: Monitor disk health.
    ```bash
    smartctl -a /dev/sdX
    ```
  - `hdparm`: Manage disk power and performance.
    ```bash
    hdparm -I /dev/sdX
    ```

---

#### **20.5 The Software Side of Storage**
- **Storage Stack**:
  - **Partitioning**: Dividing disks into sections.
  - **RAID**: Redundancy or performance optimization.
  - **Logical Volume Management (LVM)**: Flexible volume management.
  - **Filesystems**: Structure for organizing data.

---

#### **20.6 Disk Partitioning**
- **MBR vs. GPT**:
  - MBR: Legacy; supports up to 2TB.
  - GPT: Modern; supports larger disks and more partitions.
- **Commands**:
  ```bash
  # Partition a disk
  parted /dev/sdX mklabel gpt
  ```

---

#### **20.7 Logical Volume Management**
- Combine multiple disks into a single volume.
- **Steps**:
  1. Create physical volumes:
     ```bash
     pvcreate /dev/sdX
     ```
  2. Create a volume group:
     ```bash
     vgcreate my_vg /dev/sdX
     ```
  3. Create a logical volume:
     ```bash
     lvcreate -L 10G -n my_lv my_vg
     ```

---

#### **20.8 RAID: Redundant Arrays of Inexpensive Disks**
- **RAID Levels**:
  - **RAID 0**: Striping for performance.
  - **RAID 1**: Mirroring for redundancy.
  - **RAID 5/6**: Parity for fault tolerance.
- **Software RAID**:
  ```bash
  mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdX /dev/sdY
  ```

---

#### **20.9 Filesystems**
- **Traditional Filesystems**:
  - **UFS**: Unix-based systems.
  - **ext4**: Default for Linux.
  - **XFS**: High-performance alternative.
- **Next-Generation Filesystems**:
  - **ZFS**: Advanced features like snapshots, error detection.
  - **Btrfs**: Linux-native; supports subvolumes and snapshots.

---

#### **20.12 ZFS: All Your Storage Problems Solved**
- **Features**:
  - Copy-on-write for data integrity.
  - Snapshots for quick backups.
- **Example**:
  ```bash
  # Create a ZFS pool
  zpool create mypool /dev/sdX
  ```

---

#### **20.14 Data Backup Strategy**
- **Approaches**:
  - Full, incremental, or differential backups.
  - Use tools like `rsync`, `tar`, or ZFS snapshots.
- **Example**:
  ```bash
  # Backup with rsync
  rsync -av /source /backup
  ```

---

This summary highlights storage essentials and commands. Let me know if you need deeper explanations or specific examples!