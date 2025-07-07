# 🟥 RED - PicoCTF Forensics Challenge

**Author:** Shuailin Pan (LeConjuror)  
**Category:** Forensics  
**Description:**  
> RED, RED, RED, RED  
> Download the image: `red.png`

---

## 🧩 Challenge Objective

Given a suspicious image file `red.png`, extract the hidden flag using forensic techniques.

---

## 🧰 Tools Used

- `file`
- `strings`
- `exiftool`
- `zsteg`
- `base64` decoding (via terminal or Python)

---

## 🧪 Step-by-Step Process

### ✅ Step 1: Verify File Type

```bash
file red.png
```

**Output:**
```
red.png: PNG image data, 128 x 128, 8-bit/color RGBA, non-interlaced
```

It’s a valid PNG image with 8-bit RGBA encoding.

---

### ✅ Step 2: Check for Readable Strings

```bash
strings red.png
```

**Interesting Output:**
```
tEXtPoem
Crimson heart, vibrant and bold,
Hearts flutter at your sight.
Evenings glow softly red,
Cherries burst with sweet life.
Kisses linger with your warmth.
Love deep as merlot.
Scarlet leaves falling softly,
Bold in every stroke.
```

Looks like a poem hidden in metadata. Possibly a clue.

---

### ✅ Step 3: Check Metadata for Hidden Clues

```bash
exiftool red.png
```

**Key Output:**
```
Poem: Crimson heart, vibrant and bold, ...
```

First letters of each line spell:
```
C H E C K K L S B
```

🧠 That’s the clue: **CHECK LSB** (Least Significant Bit steganography)

---

### ✅ Step 4: Check for LSB Steganography using zsteg

```bash
zsteg red.png
```

**Important Output:**
```
b1,rgba,lsb,xy .. text: "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="
```

Multiple instances of the same **base64-encoded string** found in the least significant bits of the RGBA channel.

---

### ✅ Step 5: Decode the Base64 Payload

Using bash:
```bash
echo 'cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==' | base64 -d
```

Or Python:
```python
import base64
data = "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="
print(base64.b64decode(data).decode())
```

**Decoded Output:**
```
picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
```

---

## 🚩 Final Flag

```
picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
```

---

