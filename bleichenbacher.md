# Bleichenbacher Attack  
http://archiv.infsec.ethz.ch/education/fs08/secsem/bleichenbacher98.pdf  
PKCS#1 tells how data is packed before we encrypt.  

2 bytes of 0x00 0x02  
Padding(at least 8 bytes) of **n - |M| - 3**  
A 0x00 in padding means end of padding.  
M starts after that.  
One can get encrypted message **e** and multiply with **s** such that after decryption it conforms to PKCS#1.  
i.e. first 2 bytes are 0x00 0x02.
