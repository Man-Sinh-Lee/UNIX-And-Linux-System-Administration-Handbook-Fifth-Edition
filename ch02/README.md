### Summary of Chapter 2: Booting and System Management Daemons

Here is a detailed summary of the requested sections, including relevant examples and commands where applicable.

---

### **2.1 Boot Process Overview**
- The boot process involves initializing hardware, loading the OS kernel, running startup scripts, and activating system daemons.
- Modern systems rely on **UEFI** firmware for booting instead of traditional BIOS, offering enhanced flexibility and compatibility.
- The boot loader loads the kernel into memory, which initializes and transitions to user-space processes.

Example:
```bash
# View kernel boot options in GRUB
grep CMDLINE /etc/default/grub
```

---

### **2.2 System Firmware**
- Firmware executes initial boot code stored in ROM.
- **BIOS**: Legacy firmware; reads the Master Boot Record (MBR).
- **UEFI**: Modern standard, replaces BIOS with advanced features like GPT partitioning.
- Configurations, like boot order, are often managed using firmware utilities or tools like `efibootmgr`.

Example:
```bash
# Display UEFI boot entries
efibootmgr -v
```

---

### **2.3 Boot Loaders**
- Boot loaders bridge firmware and OS by loading the kernel and passing configuration parameters.
- Linux systems commonly use **GRUB**, while FreeBSD relies on its custom boot loaders.

Example:
```bash
# Boot into single-user mode using GRUB
grub> linux /vmlinuz root=/dev/sda1 ro single
grub> boot
```

---

### **2.4 GRUB: The Grand Unified Boot Loader**
- GRUB 2 is the standard boot loader for Linux distributions.
- Configuration stored in `/etc/default/grub` and `/boot/grub/grub.cfg`.
- Use `update-grub` or `grub2-mkconfig` to regenerate the GRUB configuration file.

Example:
```bash
# Regenerate GRUB configuration
update-grub
```

---

### **2.5 The FreeBSD Boot Process**
- FreeBSD uses a multi-stage boot loader (`boot0`, `loader`) similar to GRUB.
- On UEFI systems, the boot loader resides at `/boot/bootx64.efi`.
- Customizations are made in `/boot/loader.conf`.

Example:
```bash
# Add a kernel module to FreeBSD loader
echo 'snd_hda_load="YES"' >> /boot/loader.conf
```

---

### **2.6 System Management Daemons**
- `init` is the first user-space process (PID 1).
- Responsibilities include managing system runlevels and starting/stopping services.

Example (viewing systemd processes):
```bash
# List active services
systemctl list-units --type=service
```

---

### **2.7 Systemd in Detail**
- Modern replacement for `init`, used in most Linux distributions.
- Uses unit files for managing services, sockets, and other resources.
- Dependencies and parallelism improve startup efficiency.

Example:
```bash
# Enable a service to start at boot
systemctl enable apache2.service
```

---

### **2.8 FreeBSD Init and Startup Scripts**
- FreeBSD uses a traditional `init` system with `/etc/rc.d/` scripts to manage services.
- Configurations are stored in `/etc/rc.conf`.

Example:
```bash
# Enable a service in FreeBSD
echo 'sshd_enable="YES"' >> /etc/rc.conf
```

---

### **2.9 Reboot and Shutdown Procedures**
- Linux: Use `systemctl reboot` or `shutdown` commands.
- FreeBSD: Commands include `shutdown -r` or `reboot`.

Example:
```bash
# Schedule a reboot in 10 minutes
shutdown -r +10 "System rebooting in 10 minutes."
```

---

### **2.10 Stratagems for a Non-Booting System**
- Common recovery techniques include booting into single-user mode or using a live CD/USB.
- GRUB: Modify boot parameters to troubleshoot.
- FreeBSD: Use `boot -s` to enter single-user mode.

Example:
```bash
# GRUB recovery mode
grub> linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
grub> boot
```

---

Let me know if you need further details or explanations for any section!