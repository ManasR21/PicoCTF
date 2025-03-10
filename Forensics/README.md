# PicoCTF Forensics Notes

## Common Tools for Forensic Challenges

### 🔍 Basic File Inspection
- **`file <filename>`**: Identify file type.
- **`exiftool <filename>`**: Extract metadata (like creation date, software used, hidden comments).
- **`strings <filename>`**: Extract readable ASCII strings that may contain hidden information.

### 🛠️ Advanced File Analysis
- **`binwalk <filename>`**: Identify embedded files or data.
- **`xxd <filename>`**: Hex dump for manual inspection of hidden data.
- **`tail -n 20 <filename>`**: Check if data is appended after the file's end.

### 🕵️ Steganography Tools
- **`zsteg <filename>`**: Analyze PNG and BMP files for hidden data.
- **`steghide`**: Extract hidden data from files (supports JPEG, BMP, WAV, AU).
- **`stegsolve`**: GUI tool for analyzing image layers and hidden content.

### 🚩 Common Steps for Forensic Challenges
1. **Identify File Type** using `file`.
2. **Extract Metadata** using `exiftool`.
3. **Check for Readable Strings** using `strings`.
4. **Search for Embedded Files** with `binwalk`.
5. **Analyze for Hidden Data** using steganography tools like `zsteg` or `stegsolve`.
6. **Check for Appended Data** using `tail` or manual hex analysis.

---
