# 🪟 Windows Forensics — FTK Imager

## 📋 Overview

Using FTK Imager to create a forensic image of a USB drive, verify its integrity via hashing, and explore the image to recover deleted data.

### 💾 1. Forensic Image Acquisition

Created a forensic image of a 7GB USB drive using FTK Imager. Selected Physical Drive as the source to capture the entire disk, including unallocated space — not just visible files. Confirmed the correct source (PHYSICALDRIVE1, 7GB) against the internal drive (PHYSICALDRIVE0, 1TB) before proceeding. Used E01 format with automatic post-acquisition verification enabled.

### 🔑 2. Hash Verification

The computed hash (calculated from the source drive during acquisition) matched the stored verification hash (calculated from the resulting image file), confirming the image is a bit-for-bit, unaltered copy of the original USB drive.

<img width="702" height="461" alt="image" src="https://github.com/user-attachments/assets/fe65010c-06cd-4ff6-b85c-8653fcef41a5" />

### 🔍 3. Exploring the Evidence

Although the USB appeared empty when checked normally through File Explorer, browsing the image in FTK Imager revealed numerous files still physically present on the drive, marked with a red "X" icon indicating deleted status. Recovered file names included documents (Document.rtf, biology group project.pdf), screenshots, and images — none of which were visible through normal OS-level access.

This confirms the same principle observed in the earlier Linux forensic deletion exercise: deleting a file only removes its reference from the filesystem (its directory entry/pointer) — the underlying data remains physically intact and recoverable until that space is overwritten by new data.

🕰️ Oldest file found: biology group project.pdf, with a Date Created of 7/8/2023 2:05:12 PM.

<img width="1211" height="650" alt="image" src="https://github.com/user-attachments/assets/fb5fb76c-c800-4bba-9cc0-be06852466ba" />

### 🧹 4. Secure Wipe

To ensure recovered data like this is no longer accessible, the drive must be securely wiped by overwriting every sector with zeros (or random data) — the same principle demonstrated in the earlier Linux dd if=/dev/zero exercise, but applied to the entire drive rather than a single file. Simply reformatting a drive through Windows is not sufficient, since formatting (like file deletion) typically only clears filesystem references rather than overwriting the actual data — which is exactly why the deleted files above were still recoverable despite the drive "appearing" empty.
