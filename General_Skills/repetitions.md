# CTF Writeup: repetitions

**Hint:** Multiple decoding is always good.

## Description
The challenge provided an encoded file named `enc_flag`. The initial inspection showed it was a text file, and using `exiftool` revealed basic metadata without much information about the content.

## Approach
1. **File Inspection:**
   - Ran the `file` command to confirm it was an ASCII text file.
   - Used `exiftool` to check metadata, but nothing significant was found.
   - Viewed the content using `cat` and identified that the data was base64 encoded.

2. **Decoding Process:**
   - Noticed the hint suggesting multiple decodings.
   - Used an online base64 decoder and manually decoded the text multiple times.
   - After several iterations, the final decoded text revealed the flag.

## Flag
```
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_4557ec3e}
```

## Conclusion
The challenge emphasized understanding and persistence in tackling multiple layers of encoding. Utilizing base64 decoders efficiently was key to solving the problem.

