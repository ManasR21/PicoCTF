# strings it

**Author:** Sanjay C / Danny Tunitis

## Description
> Can you find the flag in file without running it?

## Approach and Steps Taken

### 1. Initial File Analysis with `exiftool`
The first step was to gather metadata about the file using the `exiftool` command:

```bash
exiftool strings
```

**Key Output:**
- File Type: ELF shared library
- Architecture: 64-bit, AMD x86-64
- MIME Type: application/octet-stream

No immediate clues about the flag were found in the metadata.

### 2. Deeper Analysis with `binwalk`
To inspect embedded files or data within the binary, `binwalk` was used:

```bash
binwalk strings
```

**Key Output:**
- Multiple Microsoft executable segments and ESP32 images were detected.

Attempted extraction with:

```bash
binwalk -e strings
```

However, extraction failed with the warning:
> "One or more files failed to extract: either no utility was found or it's unimplemented."

### 3. Attempting to Extract Strings Directly
Given the file type, `strings` was used to extract printable strings from the file:

```bash
strings strings
```

This yielded many strings, but the flag wasn’t immediately obvious.

### 4. Filtering for Potential Flag Keywords
To narrow down the search, `grep` was utilized with a focus on common flag identifiers:

```bash
strings strings | grep -iE "flag|picoCTF|key"
```

**Key Discovery:**
- The flag was successfully identified as:

```
picoCTF{5tRIng5_1T_d66c7bb7}
```

## Conclusion
The flag was embedded as a printable string within the file. Despite initial attempts using `exiftool` and `binwalk`, the effective method was directly filtering the output of `strings` with `grep` to search for common flag patterns.

---


