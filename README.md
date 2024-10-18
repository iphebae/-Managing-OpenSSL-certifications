# -Managing-OpenSSL-certifications
OpenSSL  can be used to create certificates.  OpenSSL provides functionality for creating cryptographic signatures, symmetric encryption and asymmetric (public key) encryption. It supports various ciphers and elliptic curves.
STEPS
 check openssl version: it has a different version so we have to know the version we are working with. Openssl version
 create directory to save keys : mkdir keys
 generate asymmetric encryption keys: openssl genrsa -out corp.iphebae.com.key 2048
 run ls to verify the creation of the file
 show the certification : cat corp.iphebae.com.key
  extract public key : openssl rsa -in corp.iphebae.com.key -pubout -out corp.iphebae.com_public.key
 Generate a certificate signing request : openssl req -new -key corp.gomycode.com.key -out corp.iphebae.com.csr
 verify the certificate request : openssl req -text -in corp.iphebae.com.csr -noout -verify 
generate a self-signed certificate :  openssl req -newkey rsa:2048 -nodes -keyout corp.iphebae.com.key -x509 -days 365 -out corp.iphebae.com.crt
convert the keys format : openssl pkcs12 -export -name "corp.iphebae.com" -out corp.iphebae.com.pfx -inkey corp.iphebae.com.key -in corp.iphebae.com.crt

