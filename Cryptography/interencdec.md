# Cryptography Challenge: interencdec

## Challenge Overview
- **File Name:** `enc_flag`
- **Hint Provided:** "Engaging in various decoding processes is of utmost importance."
- **File Type:** Plain text (`.txt`)

---

## Solution Steps

### 1. Initial File Analysis
- Used the `exiftool` to confirm the file was a plain text file.
- Viewed the content with PowerShell:
  ```powershell
  Get-Content .\enc_flag
  ```
- **Content Found:**
  ```
  YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==
  ```
  This resembled a Base64 encoded string.

### 2. First Base64 Decoding
- Used **CyberChef** to decode the Base64 string.
- **Result:**
  ```
  b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='
  ```
  - The `b'...'` prefix indicates a byte string.
  - The inner content looked like Base64 again.

### 3. Second Base64 Decoding
- Used **CyberChef** again to decode the second Base64 string.
- **Result:**
  ```
  wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
  ```
  - The content resembled an encrypted flag.

### 4. Decryption Attempt
- The string inside `{}` looked like it could be a Caesar cipher.
- Used **CyberChef** to try ROT13 decryption and brute-force different Caesar cipher shifts.
- **Successful Decryption with Shift 19:**
  ```
  picoCTF{caesar_d3cr9pt3d_78250afc}
  ```

---

## Final Flag
```
picoCTF{caesar_d3cr9pt3d_78250afc}
```

---

## Tools Used
- **PowerShell** for initial file viewing.
- **CyberChef** for Base64 decoding and ROT13/Caesar cipher analysis.
- **ExifTool** for initial file inspection.

---

## Conclusion
This challenge involved multiple layers of encoding and encryption:
1. **Base64 Decoding (twice using CyberChef).**
2. **Caesar Cipher Decryption (Shift 19 using CyberChef).**

Persistence and systematic decoding were key to solving this cryptography challenge.

