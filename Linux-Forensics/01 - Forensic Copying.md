## Forensic Copying 

The most basic forensic operation is copying evidence in a forensically sound manner. This means that not even one bit is allowed to be changed, otherwise, the evidence is not admissible. 

There are two main ways to copy a file in Linux:

## Using cp command

For this I created a file name cyber.txt and then copied the contents into copyfile.txt. 
And then I did the md5 hash for it and both of them gave me the same hash.

<img width="292" height="92" alt="image" src="https://github.com/user-attachments/assets/f5e109e1-2662-4560-98a4-39b22dcfa8e6" />
<img width="395" height="130" alt="image" src="https://github.com/user-attachments/assets/a2874c47-05aa-43d3-abf4-4588fce3837b" />

The hashes are the same because the cp command created an identical copy of the file contents. However, cp is not considered forensically sound because it is designed for normal file copying rather than forensic evidence collection. It only copies the selected file and does not preserve all possible evidence that may exist on a storage device, such as deleted data, hidden information, or other filesystem details. Therefore, while the copied file is identical, the method itself is not suitable for complete forensic investigations.





