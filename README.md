[![LibreELEC Logo](https://forum.libreelec.tv/core/images/style-3/pageLogo.png)](https://libreelec.tv/downloads/)

# LibreELEC 12.0.2 with Kodi (Omega) v21.2

[Download Here](https://pixeldrain.com/u/pnKSQHWg)

# Dual Boot LibreELEC

This guide helps you set up a dual boot system with LibreELEC on your laptop or PC. LibreELEC is ideal for creating a media center with Kodi.

---

## Installation Steps

### 1. Partition Preparation

#### If Using **Windows**:
- Use [MiniTool Partition Wizard](https://www.partitionwizard.com/download.html), because **Windows Disk Management cannot create EXT4 partitions**.

#### If Using **Linux**:
- Use tools like `GParted` or `KDE Partition Manager`.

### 2. Create Two Partitions:

| Label       | Format | Minimum Size | Purpose                                                                  |
|-------------|--------|--------------|--------------------------------------------------------------------------|
| `LIBREELEC` | FAT32  | 300 MB       | Stores LibreELEC boot files                                              |
| `STORAGE`   | EXT4   | 1 GB         | Stores userdata (themes, profiles, sources, thumbnails, databases, etc.) |

### 3. Extract LibreELEC

- Extract the contents of `LIBREELEC.zip` to the `LIBREELEC` partition.

### 4. Edit Boot Configuration

- Edit the `syslinux.cfg` file located in the `LIBREELEC` partition.
- Replace the `UUID` values for the `LIBREELEC` and `STORAGE` partitions with the correct ones from your system.

#### How to Check UUIDs:

- **Windows:** Use [DiskGenius](https://www.diskgenius.com/download.php)
- **Linux:** Run the following command in the terminal:
  ```bash
  blkid
  ```

---

## Recommended Boot Manager

### Using GRUB
LibreELEC can be booted using GRUB, but it requires some manual configuration.

### **Recommended: Use rEFInd**
- Easier to configure and user-friendly interface.
- Official Guide: [rEFInd Installation Guide](https://www.rodsbooks.com/refind/installing.html)
- For Windows users looking for a quick solution, check this repository:
  👉 [My rEFInd Repository](https://github.com/GilangAlRusliadi/rEFInd)

---

## Using Second Monitor as Main Display for Kodi

If you're using a laptop and want Kodi to show on an external monitor (e.g., HDMI), add the following line **after** `portable quiet` in `syslinux.cfg`:

```bash
video=HDMI-2:1920x1080@60 video=eDP-1:d
```

Explanation:
- `HDMI-2` is the external display interface (you can check with `xrandr` or `dmesg | grep -i hdmi`)
- `eDP-1:d` disables the laptop's built-in screen

---

## Additional Notes

- Always back up your data before modifying partitions.
- If boot issues occur, double-check UUIDs and partition labels.
- The official LibreELEC installer will format an entire disk, so you cannot choose a specific partition for installation or set up a dual boot. [👉 Check](https://wiki.libreelec.tv/configuration/dual-boot)

---

Happy media-centering! 🎉
