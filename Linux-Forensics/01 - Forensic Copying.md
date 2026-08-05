## Forensic Copying 

The most basic forensic operation is copying evidence in a forensically sound manner. This means that not even one bit is allowed to be changed, otherwise, the evidence is not admissible. 

## There are two main ways to copy a file in Linux:

## 1. Using cp command

For this I created a file name cyber.txt and then copied the contents into copyfile.txt. 
And then I did the md5 hash for it and both of them gave me the same hash.

<img width="292" height="92" alt="image" src="https://github.com/user-attachments/assets/f5e109e1-2662-4560-98a4-39b22dcfa8e6" />
<img width="395" height="130" alt="image" src="https://github.com/user-attachments/assets/a2874c47-05aa-43d3-abf4-4588fce3837b" />

The hashes are the same because the cp command created an identical copy of the file contents. However, cp is not considered forensically sound because it is designed for normal file copying rather than forensic evidence collection. It only copies the selected file and does not preserve all possible evidence that may exist on a storage device, such as deleted data, hidden information, or other filesystem details. Therefore, while the copied file is identical, the method itself is not suitable for complete forensic investigations.


## 2. Using dd

Similarly I created a file named attack.txt and then used dd to forensically copy the file. 

<img width="375" height="270" alt="image" src="https://github.com/user-attachments/assets/aabd8559-128a-4766-a2d0-00b3c56fb3a3" />

The dd command is considered forensically secure because it performs a low-level copy of data, creating an exact duplicate of the source. Unlike normal file copying methods, dd can copy data byte-by-byte and can be used to create complete forensic images of storage devices. This allows investigators to preserve evidence without modifying the original data. When used for forensic acquisition, the copied image can be verified using hashing algorithms to prove that it is an exact copy of the original evidence.








