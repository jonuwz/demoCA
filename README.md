# demoCA
These scripts create a demoCA, a demo intermediate CA, and scripts to create certificates with subjectAltNames.  
  
This is **NOT** (currently?) production grade. These is little to no error checking in these scripts.  
The intended use is to quickly and easily create a root CA, an intermediate, and certs that you can volume mount into docker containers.

## Attribution
The majority of the heavy lifting is done by the openssl configuration taken from [jamielinux.com](https://jamielinux.com/docs/openssl-certificate-authority/introduction.html).  
This is [copyrighted](https://jamielinux.com/docs/openssl-certificate-authority/copyright.html) under the [Creative Commons Attribution-Sharealike](https://creativecommons.org/licenses/by-sa/4.0/) license.  
Parts of the copyrighted content have been modified.

## License
This is also licensed under the [Creative Commons Attribution-Sharealike](https://creativecommons.org/licenses/by-sa/4.0/) license. 

## Usage

1. Create a root CA
```bash
./createCA
```

2. Create an intermediate CA
```bash
./createIntermediate
```

3. Create a certificate
```bash
./createServerCert -cn myhost -san myotherhost -san myotherotherhost -ip 127.0.0.1

The following resources have been created :

privatekey                                                       : bundles/myhost/key.pem
certificate                                                      : bundles/myhost/cert.pem
certificate + intermediate                                       : bundles/myhost/chain.pem
privatekey + certificate + intermediate                          : bundles/myhost/all-in-one.pem
intermediate                                                     : bundles/myhost/intermediate.pem
```

