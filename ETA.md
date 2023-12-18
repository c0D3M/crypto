Encrypted Traffic Analysis:
TLS provide authenticty(verify server cert) , confidentiality(AES) and integrity(MAC).
Most of internet traffic is now HTTPS, while this is good news for end user, it also make atackers to use encrypted channel for all kind of ransomware, malware etc etc, which if encrypted is hard to detect.
In this blog post we will discuss various technique employed by security companies to detect the presence of malware in ecncrypted traffic without decrypting them.
One option is to use middlebox (tls proxies or Application Level Gateway), this terminate the client side TLS connection, analsyse the traffic and re-encrypt and transmit, but this greatly breach use privacy.
We can extract Inter-arrival-time, packet-length, number of ACK packets, observed, number of retransmissions, round trip time. libprotoident can do
Neural Network can also be used.
Someinformation can be extracted by inspection client server TLS exchange and certificate.


1. application identification, protocol: can be done using port#, AI/ML classifer, knn, model, kmeans, auto-class.Convulution Neural Network,
2. Application type:AI/ML classifier like Adaptive boosting, Naives, Bayes, 
3. network analytics, 
4. user information identification, 
5. detection of encrypted malware, public data set"Malware Capture Facility Project, classic ML vs DeepLearning
6. file/device/website/location fingerprinting : entropy of a file can be calculated, and matches against databse of wel known files , and we use Random forest ML algorithm to match. Website Fngerprinting
7. DNS tunnelling detection : getPayLoadd.malware.com -> CNAM xyz.maware.com and keep doing and get entire malware , Firewall cant do much as its a regular DNS traffic
   To fix this use reverse proxy or analyzse contents.

- Machine Learning
- Entropy Based
- In TLS1.3, Firewall can extablish connection and then get access to certificate and then use that to analyze.
