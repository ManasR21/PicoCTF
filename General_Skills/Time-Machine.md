# picoCTF: Time Machine - Writeup

## Challenge Description
"This is what I was working on, but I'd need to look at my commit history to know why..."

## Approach
1. **Exploring the Given Files**  
   The challenge provided a file named `message.txt` containing the following text:
   > This is what I was working on, but I'd need to look at my commit history to know why...

2. **Analyzing Git History**  
   The hint pointed towards checking the commit history. Using the `git log` command, the following commit information was found:
   ```bash
   git log
   ```
   Output:
   ```
   commit b92bdd8ec87a21ba45e77bd9bed3e4893faafd0f (HEAD -> master)
   Author: picoCTF <ops@picoctf.com>
   Date:   Sat Mar 9 21:10:29 2024 +0000

       picoCTF{t1m3m@ch1n3_5cde9075}
   ```

3. **Extracting the Flag**  
   The flag was revealed directly in the commit message.

## Flag
```
picoCTF{t1m3m@ch1n3_5cde9075}
```

## Conclusion
This challenge demonstrated the importance of inspecting version control histories, as sensitive information like flags can sometimes be unintentionally exposed in commit messages.

