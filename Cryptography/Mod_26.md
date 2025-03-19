# Mod 26 - PicoCTF Challenge

**Author:** Pandu  

## Description  
Cryptography can be easy, do you know what ROT13 is?  
```
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}
```

## Solution  
This challenge suggests using **ROT13**, which is a simple Caesar cipher with a shift of 13. Applying ROT13 to the given text reveals the flag.

### Step 1: Decode ROT13  
Using an online ROT13 decoder or a simple Python script:

```python
import codecs
cipher_text = "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_jdJBFOXJ}"
flag = codecs.decode(cipher_text, 'rot_13')
print(flag)
```

### Step 2: Retrieve the Flag  
After applying ROT13, we obtain:

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_wqWOSBKW}
```

### Final Flag  
```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_wqWOSBKW}
```

## Takeaways  
- **ROT13** is a simple substitution cipher that shifts letters by 13 places.
- Applying ROT13 twice returns the original text.
- Many CTF challenges use basic cryptography techniques like ROT13 to introduce encryption concepts.

---

**Challenge Solved! ✅**

