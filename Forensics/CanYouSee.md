# CanYouSee - CTF Challenge Writeup

**Author:** Mubarak Mikail

## Description
> How about some hide and seek?  
> Download this file here.

---

## Approach and Solution

### 1. Initial Analysis
- The provided file was a ZIP archive named `unknown.zip`.
- Upon extraction, it revealed a folder named `unknown` containing a single image file: `ukn_reality.jpg`.

### 2. Metadata Inspection
- To investigate any hidden information, I used the `exiftool` to analyze the metadata of the image:

```bash
exiftool ukn_reality.jpg
```

- The key findings were:
  - The image appeared normal with standard metadata entries.
  - However, an interesting field stood out:

```
Attribution URL : cGljb0NURntNRTc0RDQ3QV9ISUREM05fYTZkZjhkYjh9Cg==
```

### 3. Base64 Decoding
- The value in the `Attribution URL` field looked like **Base64** encoded text.
- I decoded it using the following command:

```bash
echo 'cGljb0NURntNRTc0RDQ3QV9ISUREM05fYTZkZjhkYjh9Cg==' | base64 --decode
```

- The output revealed the flag:

```
picoCTF{ME74D47A_HIDD3N_a6df8db8}
```

---

## Conclusion
- The flag was hidden within the metadata of the JPEG file, specifically under the `Attribution URL` field.
- Recognizing the Base64 pattern and decoding it led directly to uncovering the flag.

---

## Tools Used
- `exiftool` - For extracting metadata from the image.
- `base64` - For decoding the Base64 encoded string.

**Final Flag:** `picoCTF{ME74D47A_HIDD3N_a6df8db8}`

---

## Lessons Learned
- Always inspect metadata when analyzing files for hidden information.
- Recognizing common encoding patterns (like Base64) is crucial for CTF challenges.

