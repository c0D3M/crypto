# crypto
- POODLE (Padding Oracle On Downgraded Legacy Encryption)  
https://www.openssl.org/~bodo/ssl-poodle.pdf  
CVE-ID: CVE­2014­3566  
Mitigation: Disabled SSL3.0 fallback & TLS_FALLBACK_SCSV  
ClientHello cannot be changed as it is cryptographically protected in Finished message.  
Client starts a TLS 1.2 session but an active attacker downgrades the connection to SSLv3.0. SSLv3.0 uses CBC or Stream Cipher RC4 mode.  
In CBC mode  
Bi XOR Ei-1 = Mi  
Encrypt(Mi) = Ci  

Now replace Cn by Ci and if server accpets it.  
D(Cn) XOR En-1 = 7th Byte  
D(Cn) = 7th XOR En-1  
D(Cn) = Mi , because we have replaced it. Mi = Bi XOR Ei-1  
Bi XOR Ei-1 = 7th XOR En-1  
Bi = 7th XOR En-1 XOR Ei-1  
thats how we can determine last byte of block B. Similary create another block to retrive other bytes.  

- BEAST

- CRIME
- FREAK
- LogJam
- BREACH
- Bleichenbacher
- Spectre, Meltdown, 
- Heartbleed
CVE-2014-0160  
http://heartbleed.com/  
In TLS Handshake, we have payload and length, payload can be 1 byte and length can be 65K.  
openssl implemntation never check length field with actual payload length and blindly return asked length data and thereby leaking information present in openssl memory which attacker shouldnot have known.  
