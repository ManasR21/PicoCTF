
# 🔄 Endianness - PicoCTF Challenge

**Author:** Nana Ama Atombo-Sackey  
**Category:** Binary Exploitation / Reversing  
**Description:**  
> Know of little and big endian?  
> Source: `nc titan.picoctf.net 57472`

---

## 🧩 Challenge Overview

This challenge presents a randomly generated 5-character word and asks for its:

- **Little Endian** hexadecimal representation
- **Big Endian** hexadecimal representation

If both are correct, the flag is revealed.

---

## 🧠 Endianness Refresher

- **Big Endian**: stores bytes in the order you read them (normal).
- **Little Endian**: stores bytes in reverse order.

---

## 🧪 Example Challenge Walkthrough

### 📝 Step 1: Get the Word

When connecting:

```
$ nc titan.picoctf.net 57472

Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
Word: ybgpf
```

---

### 🧮 Step 2: Convert Word to ASCII Hex

Word: `ybgpf`  
Characters and ASCII Hex:
```
y  → 79  
b  → 62  
g  → 67  
p  → 70  
f  → 66
```

---

### 🔁 Step 3: Endian Representations

#### ✅ Little Endian (reversed):  
Reverse the word → `fpgby`  
Convert to hex → `66 70 67 62 79`  
Result:  
```
6670676279
```

#### ✅ Big Endian (normal):  
Original word → `ybgpf`  
Convert to hex → `79 62 67 70 66`  
Result:  
```
7962677066
```

---

### 💡 Step 4: Submit and Capture the Flag

```
Enter the Little Endian representation: 6670676279
Correct Little Endian representation!
Enter the Big Endian representation:    7962677066
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_28329f0a}
```

---

## 🚩 Final Flag

```
picoCTF{3ndi4n_sw4p_su33ess_28329f0a}
```

---


