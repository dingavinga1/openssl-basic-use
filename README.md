# OpenSSL
## What is OpenSSL?
OpenSSL is an open-source tool for cryptography- mainly SSL and TLS. It is a powerful tool when and supports all kinds of functionalities- from key generation to client/server tests. 

## Use Cases
The wide range of use cases that OpenSSL covers is too wide to list here. But here are some of the top use cases.

### Assymetric key-pair generation
Assymetric encryption is an important part of today's IT infrastructure, including websites. OpenSSL supports many public key encryption algorithms. I will be covering RSA and Eliptic Curves. 

#### RSA 
Generating an RSA private key:<br/>
```openssl genpkey -algorithm RSA -out RSApriv.pem```<br/><br/>
Generating an RSA public key:<br/>
```openssl rsa -pubout -in RSApriv.pem -out RSApub.pem```<br/><br/>
Here are what the public and private keys look like:
![image](https://user-images.githubusercontent.com/88616338/223767406-f289075b-4828-4521-bbf2-a566908436cd.png)
![image](https://user-images.githubusercontent.com/88616338/223767420-7b433c3c-437f-4c62-9799-2ce13b2b8dba.png)

#### Eliptic Curve
Listing the support eliptic curves:<br/>
```openssl ecparam -list_curves```<br/><br/>
We will be using the ```secp384r1``` curve.<br/><br/>
Generating the private key:<br/>
```openssl ecparam -genkey -name secp384r1 -out ECpriv.pem```<br/><br/>
Generating the public key:<br/>
```openssl ec -in ECpriv.pem -pubout -out ECpub.pem```<br/><br/>
Here are what the public and private keys look like:
![image](https://user-images.githubusercontent.com/88616338/223768757-f596e1bd-7df4-4fff-8e12-69fac5babb78.png)
![image](https://user-images.githubusercontent.com/88616338/223768780-d78ddba7-5b2e-4bdf-a0bb-198cb24f520b.png)

### Certificate Signing Request (CSR) and generation of certificates
Generating a signing request and the signing key:<br/>
While generating this, we will be asked for our region/organization information.<br/>
```openssl req -new -newkey rsa:2048 -nodes -keyout CSRkey.pem -out CSR.pem```<br/><br/>
Generating an X509 certificate:<br/>
```openssl x509 -req -days 365 -in CSR.pem -signkey CSRkey.pem -out CSRCert.pem```<br/><br/>
Here is what the X509 certificate looks like:
![image](https://user-images.githubusercontent.com/88616338/223769978-a223063e-e0fd-4e30-b240-51f953f3b595.png)

