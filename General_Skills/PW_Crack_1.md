# PW Crack 1  
**Author:** LT 'syreal' Jones  

## Description  
Can you crack the password to get the flag?  
Download the password checker here, and you'll need the encrypted flag in the same directory too.  

## Methodology  

### 1. Understanding the Python Script  
The provided script, `level1.py`, contains a function called `str_xor`, which is used to decrypt the flag. The script follows these steps:  
- It reads the encrypted flag from `level1.flag.txt.enc`.  
- It prompts the user to input a password.  
- If the correct password `"8713"` is entered, it decrypts the flag using `str_xor`.  

The function `str_xor(secret, key)` performs an XOR operation between the encrypted flag and the key. However, instead of reverse-engineering the function, we can use the given logic to directly decrypt the flag.

---

### 2. Manually Extracting and Decrypting the Flag  
Instead of running the script interactively, we modified it to directly read the encrypted flag and decrypt it using the given key:  

```python
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

# Read the encrypted flag from the file
with open("level1.flag.txt.enc", "rb") as f:
    flag_enc = f.read().decode()

key = "8713"

decrypted_flag = str_xor(flag_enc, key)
print("Decrypted Flag:", decrypted_flag)
```

### 3. Running the Decryption Script
We executed the above Python script, which successfully decrypted the flag.
The output revealed the flag:

```
Decrypted Flag: picoCTF{545h_r1ng1ng_1b2fd683}
```
