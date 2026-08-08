# System Forensics

## 📋 Overview

This repository contains practical exercises and documentation covering the fundamentals of digital forensics. The project focuses on collecting, preserving, and analyzing digital evidence using Linux and Windows forensic tools.

The purpose of this lab is to understand how forensic investigators acquire evidence, verify its integrity, recover hidden data, and analyze system artifacts.

## 🎯 Objectives

- Understand forensic evidence handling principles
- Perform forensic file acquisition
- Verify evidence integrity using cryptographic hashes
- Compare normal file copying with forensic imaging techniques
- Securely overwrite files to prevent recovery
- Acquire and analyze volatile memory (RAM)
- Create and examine forensic disk images

## 🖥️ Environment

### Operating Systems
- Kali Linux (Virtual Machine)
- Windows

### Tools Used

- Linux command-line forensic tools
- dd (disk/data duplication)
- md5sum and SHA hashing tools
- xxd (binary file analysis)
- LiME (Linux Memory Extractor)
- FTK Imager

## 🧩 Topics Covered

### Linux Forensics
- Forensic copying using cp and dd
- Hash verification with md5sum
- Comparing forensically sound vs. non-sound copying methods
- Secure file deletion (overwriting with zeros)
- Binary file examination using xxd

### Memory Forensics
- RAM acquisition
- Volatile evidence preservation
- Basic memory analysis

### Windows Forensics
- Disk imaging
- Deleted file recovery

## 💡 Key Concepts Learned
- dd produces forensically sound bit-for-bit copies by operating at the block level, unlike cp, which only copies at the file level and can miss deleted data, slack space, and metadata.
- md5sum was used to verify that copied files were bit-for-bit identical to their originals — matching hashes confirm data integrity, while a mismatch would indicate the copy process altered the evidence.
- Deleted files remain recoverable until the underlying disk space is physically overwritten — deletion only removes the file's directory reference, not the actual data.
- Volatile memory (RAM) can contain credentials, session data, and file access traces that never touch disk and disappear permanently once the system is powered off.

## ⚠️ Disclaimer

This repository is for educational purposes only, documenting forensic techniques practiced in a personal, controlled lab environment (isolated virtual machines). All files, evidence, and data used were created or owned by me specifically for this project — no real-world systems, third-party data, or unauthorized access were involved. The techniques described here should only be applied to systems you own or have explicit permission to test.

