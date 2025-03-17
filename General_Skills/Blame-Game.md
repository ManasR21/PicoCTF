# CTF Write-Up: Git Challenge

## Challenge Overview
The task was to identify which commit introduced an issue in the program and uncover the embedded flag.

## Approach

### 1. **Inspecting Git Commit History**
To begin, I checked the commit history using the following command:

```bash
git log > got_log.txt
```

This saved the entire commit history into a file for easy inspection.

### 2. **Filtering for Potential Flags**
I then searched the log file for potential flags using `grep`:

```bash
cat got_log.txt | grep "picoCTF{"
```

This revealed the following line:

```
Author: picoCTF{@sk_th3_1nt3rn_81e716ff} <ops@picoctf.com>
```

### 3. **Analyzing the Suspicious Commit**
To further investigate, I checked the details of the commit:

```bash
git show 23e9d4ce78b3cea725992a0ce6f5eea0bf0bcdd4
```

This displayed the following diff:

```diff
commit 23e9d4ce78b3cea725992a0ce6f5eea0bf0bcdd4
Author: picoCTF{@sk_th3_1nt3rn_81e716ff} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:15 2024 +0000

    optimize file size of prod code

diff --git a/message.py b/message.py
index 7df869a..326544a 100644
--- a/message.py
+++ b/message.py
@@ -1 +1 @@
-print("Hello, World!")
+print("Hello, World!"
```

The commit introduced a syntax error by removing the closing parenthesis, causing the program to fail.

### 4. **Conclusion**
The flag for the challenge was hidden in the author's name:

```
picoCTF{@sk_th3_1nt3rn_81e716ff}
```

## Key Takeaways
- Using `git log` and `grep` can be an efficient way to filter and find hidden information in commit histories.
- Always inspect early commits when debugging issues, as they might contain the root cause.
