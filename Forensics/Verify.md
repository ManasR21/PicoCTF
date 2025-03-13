# Verify Walkthrough

**Author:** Jeffery John  

## Challenge Description
> People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.  
>
> **SSH Access:**  
> `ssh -p 63467 ctf-player@rhea.picoctf.net`  
>
> **Password:** `f3b61b38`  
> - Accept the fingerprint by typing `yes` when prompted.
> - Once connected, run `ls` to view the available files.  
>
> **Checksum:**  
> `fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7`
>
> To decrypt the file once you've verified the hash, run:
> ```bash
> ./decrypt.sh files/<file>
> ```

---

## Approach and Solution

1. **Connect to the Server**
```bash
ssh -p 63467 ctf-player@rhea.picoctf.net
```
- Enter the provided password `f3b61b38` when prompted.
- Accept the SSH fingerprint by typing `yes`.
- Run `ls` to list the files and navigate into the appropriate directory.

2. **Identify the Correct File**
- Use the `file` command to check the type of each file:

```bash
file *
```

- One of the outputs identified a file as:

```
87590c24: openssl enc'd data with salted password
```

3. **Verify the File Using SHA-256**
- Calculate the SHA-256 hash of the suspicious file:

```bash
sha256sum files/87590c24
```

- The hash matched the provided checksum:

```
fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
```

4. **Decrypt the File**
- Run the provided decrypt script with the identified file:

```bash
./decrypt.sh files/87590c24
```

- The script successfully decrypted the file and revealed the flag:

```
picoCTF{trust_but_verify_87590c24}
```

---

## Understanding the Decrypt Script (`decrypt.sh`)

```bash
#!/bin/bash

# Check if the user provided a file name as an argument
if [ $# -eq 0 ]; then
    echo "Expected usage: decrypt.sh <filename>"
    exit 1
fi

# Store the provided filename in a variable
file_name="$1"

# Check if the provided argument is a file and not a folder
if [ ! -f "/home/ctf-player/drop-in/$file_name" ]; then
    echo "Error: '$file_name' is not a valid file. Look inside the 'files' folder with 'ls -R'!"
    exit 1
fi

# Attempt to decrypt the file using OpenSSL
if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
    echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
fi
```

### Key Points:
- The script ensures a valid filename is provided and exists.
- It uses OpenSSL with the following parameters:
  - **`-d`**: Decrypt mode.
  - **`-aes-256-cbc`**: AES-256 encryption in CBC mode.
  - **`-pbkdf2`**: Uses the PBKDF2 key derivation method for added security.
  - **`-iter 100000`**: Number of iterations for the key derivation function.
  - **`-salt`**: Indicates that the encrypted file uses a salt.
  - **`-k picoCTF`**: Specifies the decryption password.

### Error Handling:
- The script checks for common errors like missing files or decryption failures and responds with helpful error messages.

---

## Final Flag
```
picoCTF{trust_but_verify_87590c24}
```

---
