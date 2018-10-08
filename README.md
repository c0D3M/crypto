# crypto
- POODLE (Padding Oracle On Downgraded Legacy Encryption)  
https://www.openssl.org/~bodo/ssl-poodle.pdf  
CVE-ID: CVE­2014­3566  
Mitigation: Disabled SSL3.0 fallback & TLS_FALLBACK_SCSV  
ClientHello cannot be changed as it is cryptographically protected in Finished message.  
Client starts a TLS 1.2 session but an active attacker downgrades the connection to SSLv3.0. SSLv3.0 uses CBC or Stream Cipher RC4 mode.  
In CBC mode  
Bi ⊕ Ei-1 = Mi  
Encrypt(Mi) = Ci  

Now replace Cn by Ci and if server accpets it.  
D(Cn) ⊕ En-1 = 7th Byte  
D(Cn) = 7th ⊕ En-1  
D(Cn) = Mi , because we have replaced it. Mi = Bi ⊕ Ei-1  
Bi XOR Ei-1 = 7th ⊕ En-1  
Bi = 7th ⊕ En-1 ⊕ Ei-1  
thats how we can determine last byte of block B. Similary create another block to retrive other bytes.  

- BEAST  
https://www.youtube.com/watch?v=-_8-2pDFvmg  
http://commandlinefanatic.com/cgi-bin/showarticle.cgi?article=art027  

Aplicable to CBC cipher , suppose we want to know Pi.  
In CBC, Pi is first masked with Ci-1 and then DES/AES is applied to get Ci. This Ci serves as IV for next block i.e. i+1).  
In CBC, we know Ci-1, Ci , suppose we now load a Chosen Plain Text (CPA) for encryption which is  
Ci ⊕ Ci-1 ⊕ Mi  
Ci will cancel out and what we have Ci-1 ⊕ Mi , which is nothing but second block encryption.  
In this way we can craft Mi , byte by byte and retrive the plain text.  



- CRIME
- BREACH
Both are related to 
- FREAK
- LogJam

- Bleichenbacher
- Spectre, Meltdown, 
- Heartbleed
CVE-2014-0160  
http://heartbleed.com/  
In TLS Handshake, we have payload and length, payload can be 1 byte and length can be 65K.  
openssl implemntation never check length field with actual payload length and blindly return asked length data and thereby leaking information present in openssl memory which attacker shouldnot have known.  
