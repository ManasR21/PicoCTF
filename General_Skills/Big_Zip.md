# Big Zip CTF Challenge Solution

**Author:** LT 'syreal' Jones  
**Challenge Name:** Big Zip

## Description
> *"Unzip this archive and find the flag."*

## Hint
> *"Can grep be instructed to look at every file in a directory and its subdirectories?"*

---

## Approach and Solution

### 1. **Unzipping the Archive**
The provided ZIP file was unzipped using the following command:

```bash
unzip file.zip -d extracted_files
```

After extraction, the directory contained **thousands of nested folders and files**, making manual inspection infeasible.

### 2. **Navigating to the Extracted Directory**

```bash
cd extracted_files
```

### 3. **Using `grep` to Search Recursively**
Given the challenge hint, `grep` was the ideal tool to search for the flag within all files and directories. The recursive option `-r` ensures that all subdirectories are also searched.

If the flag format is known (like `picoCTF{}`), the following command is effective:

```bash
grep -r "picoCTF{" .
```

### 4. **Flag Discovery**
This command successfully located the flag in a deeply nested file:

```bash
./folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

**Flag:** `picoCTF{gr3p_15_m4g1c_ef8790dc}`

### 5. **Alternative Commands**
- To avoid issues with binary files:

```bash
grep -r --binary-files=text "picoCTF{" .
```

- Using `ripgrep` (if installed) for faster searching:

```bash
rg "picoCTF{" .
```

---

## Conclusion
The challenge highlighted the power of `grep` for recursive searches in large directory structures. Knowing the flag's format significantly streamlined the search process.

`grep` proved to be a simple yet powerful tool for efficient text searching in Capture The Flag (CTF) challenges.

