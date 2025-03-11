# picoCTF: Super SSH - Writeup

## Challenge Description
Using a Secure Shell (SSH) is going to be pretty important.
Can you ssh as `ctf-player` to `titan.picoctf.net` at port `49168` to get the flag?
You'll also need the password `1db87a14`. If asked, accept the fingerprint with `yes`.
If your device doesn't have a shell, you can use: [picoCTF Webshell](https://webshell.picoctf.org).
If you're not sure what a shell is, check out the [Primer](https://primer.picoctf.com/#_the_shell).

## Approach
1. **Establishing SSH Connection**  
   The SSH command to connect was:
   ```bash
   ssh -p 49168 ctf-player@titan.picoctf.net
   ```

2. **Trusting the Host**  
   Upon the first connection, SSH prompted to verify the authenticity of the host:
   > The authenticity of host '[titan.picoctf.net]:49168' can't be established.  
   > Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

   Typing `yes` added the host to the list of known hosts.

3. **Authentication**  
   The password `1db87a14` was used for authentication. Upon successful login, the following message appeared:
   > Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_45a48857}

4. **Connection Closure**  
   The connection was automatically closed after displaying the flag.

## Flag
```
picoCTF{s3cur3_c0nn3ct10n_45a48857}
```

## Conclusion
This challenge highlighted the basic usage of SSH, including connecting via a non-standard port, authenticating with a password, and verifying host authenticity during the first connection.

