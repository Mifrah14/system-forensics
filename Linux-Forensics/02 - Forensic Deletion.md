## Forensic Deletion


When files are deleted by the user, the data does not magically disappear, instead, the allocated space is simply marked for free use, it then becomes inaccessible to the user by regular means. The 
forensically safe way to wipe a file is to directly overwrite it with zeros. 


<img width="595" height="797" alt="image" src="https://github.com/user-attachments/assets/3879da8c-060c-41ea-86b3-5d41ce614440" />


The original size of my file was 63 bytes which was identified using the command ls -l mytext.txt. 
The command xxd -b mytext.txt was then used to display the contents of the file in binary format.
After overwriting it became 512 bytes because dd writes data in blocks. Since no block size was specified, the default block size of 512 bytes was used. The original contents of the file cannot be retrieved because they were overwritten with zeros, replacing the original data. The xxd -b output after the overwrite confirmed that the previous contents were no longer present.

