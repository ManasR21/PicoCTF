# CTF Write-Up: Glory of the Garden

## Challenge Overview
**Title**: Glory of the Garden  
**Author**: jedavis/Danny  

**Description**:
> This garden contains more than it seems.

The objective was to investigate the provided `garden.jpg` image and uncover the hidden flag.

---

## Approach

### 1. **Inspecting Metadata with ExifTool**
The first step was to analyze the image metadata using `exiftool`:

```bash
exiftool garden.jpg
```

This provided detailed metadata about the file, but no obvious flag or suspicious information was found.

### 2. **Searching for Hidden Strings**
Next, I used the `strings` command to search for any hidden or embedded text within the file:

```bash
strings garden.jpg
```

Among the extracted strings, the following were noted:

```
M(.I
]hWP&
jc#k
=7g&
mjx/
s\]|."Ue
\qZf
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
```

The flag was identified as the last string in the list.

---

## Conclusion
The flag was successfully retrieved by combining basic metadata analysis with string extraction techniques.

### Key Takeaways:
- **ExifTool** is great for quickly checking metadata, which can sometimes include hidden clues.
- **Strings** is an essential tool for scanning binary files for readable text.

This challenge highlighted the importance of simple but effective file analysis methods in CTFs. 🚩

