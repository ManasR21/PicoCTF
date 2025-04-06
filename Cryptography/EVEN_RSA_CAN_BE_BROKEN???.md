RSA Challenge: Breaking RSA with Known N and e
==============================================

Challenge Description
---------------------

**Title:** EVEN RSA CAN BE BROKEN???**Author:** Michael Crotty

This service provides an encrypted flag. The challenge is to decrypt it given only the modulus (N) and public exponent (e).

Solution Approach
-----------------

### Understanding the Problem

*   The N value is a semi-prime (product of two primes)
    
*   Given only N and e, we need to decrypt the flag
    

### Tools Used

*   [dcode.fr RSA Cipher Tool](https://www.dcode.fr/rsa-cipher)
    

### Solution Steps

1.  The tool attempted Wiener's attack first, which failed
    
2.  Then successfully performed prime factorization of N to find p and q
    
3.  With p and q, computed the private exponent d and decrypted the flag
    

### The Flag

`  picoCTF{tw0_1$_pr!m381772be5}   `

About Wiener's Attack
---------------------

Wiener's attack is an attack on RSA when the private exponent d is too small relative to the modulus N.

**Conditions for Wiener's Attack to work:**

*   d < (1/3) \* N^(1/4)
    
*   q < p < 2q (primes are not too far apart)
    

**How it works:**

1.  Uses continued fractions to find approximations of e/N
    
2.  Looks for fractions that might reveal the private exponent d
    
3.  If d is small enough, this method can efficiently recover it
    

**Why it failed here:**

*   In this challenge, d was likely not small enough to satisfy Wiener's conditions
    
*   The primes were factorable through direct factorization methods instead
    

The successful approach was to factor N directly into its prime components p and q, which is generally the most straightforward way to break RSA when N is factorable.
