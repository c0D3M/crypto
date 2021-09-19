When a user Bob install app, this create  
  - Identity key Pair , this is long term ECHD key pair (I_Alice).  
  - Signed Pre-Key+ Signature,  a medium term ECDH key pair, signed by Identity Key Pair (S_Bob).  
  - A bunch of One-Time Pre-Key.  
Once Bob connects to whatsapp server it send  the above bundle to server.  

Session Setup:  
- Alice wants to communicate with Bob, it ask server the above bundle, note that server send one of One-Time Pre-Key(OTPK) and delete.  
  If OTPK is not present it wont send.  
- Alice generate a ECHD Ephemeral key pair E_Alice, Identity key Pair I_Alice
- Alice calculate master secret as 

     master_key = ECDH(I_Alice , S_Bob) || ECDH(E_Alice , I_Bob) || ECDH(E_Alice , S_Bob) || ECDH(E_Alice, OTPK_Bob)
     
     Last ECDH will not happen if OTPK is not present.  
     HKDF is used to generate root_key and chain_key.  
     Alice send msg + I_Alice + E_Alice  
     This above inown as X3DH.
     
- On Bob ends , it does the same to generate master key. Note that Bob uses its private key (same like DH).  

Sending Message:  
Both Alice and Bob has KDF Chain for receiving and sending message.  


