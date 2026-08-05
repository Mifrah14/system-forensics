# System Forensics

## Overview

This repository contains practical exercises and documentation covering the fundamentals of digital forensics. The project focuses on collecting, preserving, and analyzing digital evidence using Linux and Windows forensic tools.

The purpose of this lab is to understand how forensic investigators acquire evidence, verify its integrity, recover hidden data, and analyze system artifacts.

## Objectives

- Understand forensic evidence handling principles
- Perform forensic file acquisition
- Verify evidence integrity using cryptographic hashes
- Compare normal file copying with forensic imaging techniques
- Securely overwrite files to prevent recovery
- Acquire and analyze volatile memory (RAM)
- Create and examine forensic disk images
- Investigate USB device activity

## Environment

### Operating Systems
- Ubuntu Linux (Virtual Machine)
- Windows

### Tools Used

- Linux command-line forensic tools
- `dd` (disk/data duplication)
- `md5sum` and SHA hashing tools
- `xxd` (binary file analysis)
- LiME (Linux Memory Extractor)
- FTK Imager
- USBDeview

## Topics Covered

### Linux Forensics
- Forensic copying using `cp` and `dd`
- Hash verification
- File integrity checking
- Secure deletion
- Binary file examination

### Memory Forensics
- RAM acquisition
- Volatile evidence preservation
- Basic memory analysis

### Windows Forensics
- Disk imaging
- Deleted file recovery
- USB device investigation

  
## Key Concepts Learned

- Digital evidence must be collected without modification.
- Hash values are used to verify evidence integrity.
- Deleted files may still contain recoverable data.
- Volatile memory contains valuable information that disappears after shutdown.
- Proper documentation is essential during forensic investigations.

## Disclaimer

This repository is for educational purposes and demonstrates forensic techniques in a controlled lab environment.
