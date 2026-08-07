### RAM / Memory Forensics with LiME

## Overview
This section covers acquiring a forensic image of volatile memory (RAM) on a live Linux system using LiME (Linux Memory Extractor), then extracting and searching readable data from the raw dump.

Tools used: Kali Linux, LiME, strings, grep

## 1. Cloning LiME

Cloned the LiME repository to obtain the source code required to build a custom kernel module for RAM acquisition.

<img width="667" height="158" alt="image" src="https://github.com/user-attachments/assets/170afd08-1535-4369-ab41-193cd8dc4b8d" />

## 2. Building the LiME Kernel Module

Compiled LiME against the matching kernel headers, producing lime-7.0.12+kali-amd64.ko.

<img width="671" height="546" alt="image" src="https://github.com/user-attachments/assets/702c73ab-216f-419e-b990-a39e292cf507" />

## 3. Acquiring the Memory Dump

Loaded the compiled module into the kernel, dumping physical memory to memory_dump.bin in padded format (preserves physical address alignment by zero-filling memory holes). Verified the module was active and the resulting dump file was 2.0GB.

<img width="833" height="177" alt="image" src="https://github.com/user-attachments/assets/ffe5486f-fa5e-4966-92ae-e7b3364d6bc6" />

## 4. Converting the Dump to Readable Text

Extracted printable ASCII strings from the raw binary dump, producing a 181MB searchable text file.

<img width="758" height="112" alt="image" src="https://github.com/user-attachments/assets/d5e960b8-5a0c-45ca-8cd1-54fe26a29c4a" />

## 5. Searching for Artifacts

Once the raw memory dump was converted to readable text, grep was used to search for specific categories of forensically relevant data. Each search targets a different type of artifact that commonly persists in RAM — credentials, network activity, and remote access sessions — since these often exist only in memory and leave no trace on disk.

# 5.1 Passwords

grep -i "passwd" /home/mifrahkhan/Desktop/results.txt | head -20

Finding:

1. A hardcoded credential-like string was recovered: passwd='geheim$parole'
   
geheim and parole are German and French words for "secret" and "password" respectively, suggesting this originated from a script, tool, or config file using placeholder/test credentials rather than a real user-entered password.

2. Several file path references to a passwd file located on the Desktop were also recovered:

/home/mifrahkhan/Desktop/passwd

Significance:
This result demonstrates two separate but related points:

Credential persistence — plaintext, password-like strings can remain recoverable in RAM long after being processed, even without the user actively typing them at capture time.

File access traces — RAM retains references to files that were opened, listed, or referenced recently (in this case, a passwd file on the Desktop), meaning memory analysis can help reconstruct recent file activity even without disk-level logs.

<img width="592" height="372" alt="image" src="https://github.com/user-attachments/assets/10cb419a-ce24-435c-8b56-c0add85278b1" />

# 5.2 Web Activity

grep -i "http://\|https://" /home/mifrahkhan/Desktop/results.txt | head -20

Finding: No matches returned.

Significance:
A negative result is still a valid forensic conclusion. No HTTP/HTTPS references being present suggests no browser sessions, active downloads, or web requests were occurring at the exact moment the memory was captured — a useful data point if this dump were being used to establish a timeline of system activity.












