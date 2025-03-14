# CTF Challenge Write-up: Secrets-of-the-polyglot

## Challenge Description
A file named `flag2of2-final.pdf` was provided. The task was to uncover the hidden flag.

---

## Approach and Solution

1. **Initial Analysis**  
   Upon opening the PDF file, the **second half** of the flag was visible:
    ```
    1n_pn9_&_pdf_90974127}
   ```

   
2. **Metadata Examination**  
Running `exiftool` on the file revealed interesting metadata:
- The **File Type** was identified as `PNG` despite the `.pdf` extension.
- This indicated that the file might have been incorrectly labeled.

3. **Extension Change and Discovery**  
- The file extension was changed from `.pdf` to `.png`.  
- Upon opening the renamed `.png` file, the **first half** of the flag was discovered:  
  ```
  picoCTF{f1u3n7_
  ```

4. **Final Flag Assembly**  
Combining both parts resulted in the complete flag:
 ```
 picoCTF{f1u3n7_1n_pn9_&_pdf_90974127}
 ```
