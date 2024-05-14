## Secure Text Transfer Using Deffie-HellMan Key Exchange Based On Cloud

Security in the cloud has become a significant concern, garnering widespread attention. Even industry leaders such as Google and Amazon allocate substantial resources to enhance their security measures. Here, we have implemented a secure text transfer system utilizing the Diffie-Hellman key exchange algorithm.

-----

# Theory On Algorithm:

One potential method for secure data transfer involves User A encrypting the data using a key and then sharing that key with User B. While this approach offers some level of security, it remains vulnerable to third-party eavesdropping. To address this vulnerability, we sought a system where two users could independently generate the same key without directly exchanging it. This key could then be used to encrypt and decrypt the data securely. This is where the Diffie-Hellman key exchange algorithm comes into play.

The Diffie-Hellman key exchange (DH) method enables the secure exchange of cryptographic keys over a public channel. Named after Whitfield Diffie and Martin Hellman, DH was among the earliest public-key protocols developed within the field of cryptography.

In a public-key cryptosystem, encryption and decryption are governed by separate keys—typically denoted as E and D, respectively. The main principle behind DH is that computing the decryption key D from the encryption key E is computationally infeasible, requiring more computational resources than practically available (e.g., more than 10^100 instructions). This allows the encryption key E to be publicly shared without compromising the security of the decryption key D.

Each user within the network can publish their encryption key in a public directory. This enables any user of the system to send encrypted messages to any other user, ensuring that only the intended recipient can decrypt them. In essence, a public key cryptosystem serves as a multiple-access cipher, facilitating private conversations between individuals, even if they have never communicated before. Each user sends messages encrypted with the recipient's public encryption key and decrypts messages using their own private decryption key.

-----

# Algorithm:

p is a prime number,
g is a primitive root modulo of p

Step 1: Alice and Bob get public numbers P = 23, G = 9

Step 2: Alice selected a private key a = 4 and
        Bob selected a private key b = 3

Step 3: Alice and Bob compute public values
Alice:    x =(9^4 mod 23) = (6561 mod 23) = 6
        Bob:    y = (9^3 mod 23) = (729 mod 23)  = 16

Step 4: Alice and Bob exchange public numbers

Step 5: Alice receives public key y =16 and
        Bob receives public key x = 6

Step 6: Alice and Bob compute symmetric keys
        Alice:  ka = y^a mod p = 65536 mod 23 = 9
        Bob:    kb = x^b mod p = 216 mod 23 = 9

Step 7: 9 is the shared secret.    

-----

# Required Packages

```python
pip install Flask
pip install Flask-SocketIO
```

-----

# Explination Of Application And Code:

As this is a chat room one of the 2 user keys will be assigned by the server, user only have to choose the second private key and everyone who are willing to enter the chat room have to use the same private key

The user will first see the home page where they will be asked the name and then a private key

If he is the first user then he can click the create room option otherwise he can enter the room code and click on join room

There the users can see the chat area, each of the message is recorded using the time stamps

In the client side the JavaScript will encrypt the message by the user

The encrypted message will be decrypted at the client side using python which will then render it in the client side chat area 

All of the clients are maintained as sockets which will store the information related to client like name, room, private key
