# CTF Write-Up: First Find

## Challenge Overview
**Title**: First Find  
**Author**: LT 'syreal' Jones  

**Description**:
> Unzip this archive and find the file named 'uber-secret.txt'.

The objective was to extract and locate the hidden `uber-secret.txt` file from the provided zip archive.

---

## Approach

### 1. **Unzipping the Archive**
First, I extracted the contents of the downloaded archive:

```bash
unzip archive.zip
```

### 2. **Finding the File**
To locate the target file, I used the `find` command to search recursively:

```bash
find . -name "uber-secret.txt"
```

**Output:**
```
./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

The file was located deep within a hidden directory structure.

### 3. **Navigating to the File**
I navigated to the directory containing the file:

```bash
cd "./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/"
```

I verified the file's presence with:

```bash
ls
```

**Output:**
```
uber-secret.txt
```

### 4. **Reading the File Contents**
Finally, I used the `cat` command to reveal the contents of the file:

```bash
cat uber-secret.txt
```

**Flag:**
```
picoCTF{f1nd_15_f457_ab443fd1}
```

---

## Conclusion
This challenge emphasized the effectiveness of the `find` command for locating hidden files within complex directory structures. It also highlighted the importance of being thorough, especially when dealing with hidden directories.

### Key Takeaways:
- Use `find` for recursive searches in directory structures.
- Enclose paths with spaces in quotes to avoid errors.

Another flag secured! 🚩

