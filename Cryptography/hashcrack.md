
# HashCrack - PicoCTF Challenge

**Author:** Nana Ama Atombo-Sackey  

## Description  
A company stored a secret message on a server, but due to weakly hashed passwords, it was breached. Your goal is to access the secret stored within the server.

### Server Access  
To connect to the server, use:
```bash
nc verbal-sleep.picoctf.net 53299
```

## Solution Walkthrough  

### Step 1: Identifying and Cracking the MD5 Hash  
Upon connecting to the server, we receive an MD5 hash:
```bash
482c811da5d5b4bc6d497ffa98491e38
```
Using an online hash lookup (or a local hash cracking tool like Hashcat/JohnTheRipper), we determine that the password is:
```
password123
```
Entering this password confirms the crack but does not reveal the flag yet.

### Step 2: Identifying and Cracking the SHA-1 Hash  
Next, we receive an SHA-1 hash:
```bash
b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
```
Cracking this hash reveals the password:
```
letmein
```
Entering the password confirms the crack but still does not reveal the flag.

### Step 3: Identifying and Cracking the SHA-256 Hash  
The final hash given is SHA-256:
```bash
916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
```
Cracking this hash reveals:
```
qwerty098
```
Entering this password confirms the crack, and the flag is revealed!

## Final Flag  
```
picoCTF{UseStr0nG_h@shEs_&PaSswDs!_23622a7e}
```

**Challenge Completed Successfully! ✅**

