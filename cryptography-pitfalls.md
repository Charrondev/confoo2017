## Cryptography Pitfalls

* by Jogn Downey @jtdowney from Braintree owned by Paypal

#### Don't design or implement your own crypto

* For data in transit
    * Use TLS (once SSL), SSH, or VPN/IPsec
* For data at rest
    * Use GnuPG
* Data to be signed
    * Use GnuPG

#### Avoid low elvel libraries
* OpenSSL
* PyCrypto
* Bouncy Castle

#### Use a high level library
* NaCL/libsodium
* Keyczar

### Pitfalls
#### Random Number Generation
* Not suing a cryptographically secure random number generator
* Not using random data when it is required

```
int getRandomNumber() {
    return 4; // Chosen by fair dice roll
}
``` 
* Broken Random Number generators

#### Hash Functions
* Don't use cryptographically insecure hash functions (MD5, SHA1)
* Misunderstanding checksums
    * Should only be used to verify downloads didn't get corrupted
* Length Extension attacks
    * fix use an hmac function
* Recomendation
    * Use SHA-256 (SHA-2 family)
    * Choose Hmac_sha-256 if you want a signature
    * stop using MD5
    * Stop using SHA1

#### Passwords
* Don't store them
* One-way
    * Value can be used for verifications
* Randomized
* Use tunably slow algorithms
    * bcrypt, scrypt, argon2, PBDKF2
* Upgrade to something more modern
    * Don't wait for user to login and silently upgrade
    * Wrap bcrypt around existing scheme
        * use bcrypt(sha(salt + hash)) etc
        * Upgrade all passwords in place at once

#### Ciphers
* Old weak algorithms
* Using ecb mode block ciphers
    * Do not loop over cipher over appending text especially if there is any pattern in the data.
* using authenticated encryption
* Use box/secret box from NaCL/libsodium
* Stop suing DES
* Stop building your own on top of AES (its very very easy to mess up)


#### TLS/SSL
* Very certificate chain and hostname
    * Verify it goes to who you intened to connect to
    * Hostname verification is protocol dependent
        * OpenSSL doesn't have it built in
* Be sure to configure you server properly
    * [SSL Labs](https://www.ssllabs.com)
* Ensure you're validating connections
* Lean on framework/library
* Setup an automated test suite

[crypto-class](https://www.coursera.org/learn/crypto)

[Shor's algorithm](https://en.wikipedia.org/wiki/Shor's_algorithm)

[Google article](https://security.googleblog.com/2016/07/experimenting-with-post-quantum.html)