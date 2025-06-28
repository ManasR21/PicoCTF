# DISKO 1

**Author:** Darkraicg492  
**Category:** Forensics  
**Difficulty:** Easy  
**Tags:** `forensics` `disk image` `strings` `picoCTF`

---

## 📝 Description

> Can you find the flag in this disk image?  


---

## 🧠 Challenge Summary

You are given a `.gz` file which, when extracted, contains a raw disk image (`.dd`). 

---

## 🚀 Steps to Solve

1. **Extract the archive**:
    ```bash
    gunzip disko-1.gz
    ```

2. **Check the file type**:
    ```bash
    file disko-1.dd
    ```
    Output shows it’s a FAT32-formatted disk image with no partition table.

3. **Run strings directly on the disk image**:
    ```bash
    strings disko-1.dd | grep -i "picoCTF"
    ```

## 🏁 Flag

```picoCTF{1t5_ju5t_4_5tr1n9_c63b02ef}```
