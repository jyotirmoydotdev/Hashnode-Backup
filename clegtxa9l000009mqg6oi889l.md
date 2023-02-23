# Cryptography

Cryptography is a huge topic and constantly evolving as the internet get advances. Here I will explain the topics that will help you understand blockchain better. The word cryptography comes from two words the prefix `crypto` means “hidden” and the suffix `graphy` means “writing”. Cryptography is a field of study of secure communication and encryption, With it, we can secure our information and securely communicate with others on the internet as no third person can read it or misuse our data. When we encrypt some data, it can't be read by humans and even computers, to make it possible to use some algorithms like Secure Hash Algorithm (SHA), Message Digest (MD), Windows NTHash, RACE Integrity Primitives Evaluation Message Digest (RIPEMD), Whirlpool, and RSA. The most popular blockchain like Bitcoin and Ethereum use SHA256. But before we know what SHA256 is, we need to understand Hash Function or Hash.

# Hash Function

In python3 we have an inbuilt function `hash()`, which returns the hash integer value of an object, the object can be a string, integer, float, or tuple. Each object pass in the hash function has a unique and fixed-size output but the same object has the same hash value. The hash function generally outputs a fixed-size value, remember that the hash function is a one-way function, in which we can convert an object into a hash value but it is very difficult to convert a hash value to an object. The values returned by a hash function are called hash values, hash codes, digests, or simply hashes.

```python
>>> hash("Hello World!")
8733196720692250248
>>> hash("Hi")
-7322946855749321176
```

Let us understand with an example, suppose we want to store passwords in the database, we can store passwords in plain text but it will be very risky. So we can use a hash function to store passwords. In the below table, you can see the passwords are stored as a hash value. Whenever users want to access their accounts, the password first converts into a hash value and compares with a hash value that is stored in the database.

| User ID | Password |
| --- | --- |
| user1 | 8068189639244901433 |
| user2 | \-1338079075162857857 |
| user3 | \-4837162360507738362 |

This is a simple example of a hash function but there are more Hash functions like MD5 and SHA256, in the blockchain we mostly use SHA256.

# SHA256 Hash Function

SHA256 stood for **Secure Hash Algorithm 256-bit and** was designed by the United States National Security Agency and was first published in 2001. No matter how much the input size is the output will always be 64 characters string which is called a digest.

```bash
Input = "Hello World!"
7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d9069
```

Python has a built-in library called `hashlib()` which is designed to provide a common interface to different secure hashing algorithms. The module provides constructor methods for each type of hash. For example, the `.sha256()` constructor is used to create a SHA256 hash.

```python
import hashlib
password = "hello1234"
hashed_password = hashlib.sha256(password.encode('utf-8')).hexdigest()
print(hashed_password)
```

`hashlib` is a module that implements a common interface to many different secure hash and message digest algorithms. Included are the FIPS secure hash algorithms SHA1, SHA224, SHA256, SHA384, and SHA512 (defined in FIPS 180-2) as well as RSA’s MD5 algorithm (defined in Internet **RFC 1321**).

| User ID | Password |
| --- | --- |
| user1 | b9c950640e1b3740e98acb93e669c65766f6670dd1609ba91ff41052ba48c6f3 |
| user2 | d84464181f7f019f3fb10e6bbd06f543d7ac84c4f8e360ebb9402a472ab30ebc |
| user3 | 9e4095417158189ad876acbba90c1c61d5767c2e1a507910c4a37cd8a7271d12 |

Now our passwords are stored in digests, but there is a problem every time we hash an object the same digest is output, Why it is a problem? Suppose there is a database where the most used password is stored with its digest. They can use their database to search the digest and can get the password. To solve this problem we use a nonce.

| Password | Digest |
| --- | --- |
| password1234 | b9c950640e1b3740e98acb93e669c65766f6670dd1609ba91ff41052ba48c6f3 |
| 1234password | d84464181f7f019f3fb10e6bbd06f543d7ac84c4f8e360ebb9402a472ab30ebc |
| ThisIsPassword | 9e4095417158189ad876acbba90c1c61d5767c2e1a507910c4a37cd8a7271d12 |

# Nonce

In the previous article [Blockchain Structure](https://jyotirmoy.hashnode.dev/blockchain-structure#heading-block), there was a section 'Block' in which I have given a short description of Nonce, *Nonce is a random number that is used in the proof-of-work mechanism to validate the block and add it to the blockchain.* We can implement this idea to generate a different digest of the same password or object.

UUID, ***Universal Unique Identifier***, is a python library that helps in generating random objects of 128 bits as ids. `uuid.uuid4().hex` we can use this code to generate a random hash. Whenever we call `generate_hash(password)` function we create a Nonce and a Digest, which we store on our database.

```python
import uuid
import hashlib

password="hello1234"

def generate_hash(password):
    nonce=uuid.uuid4().hex # This nonce need to store in database
    hash= hashlib.sha256((password.encode('utf-8'))+nonce.encode('utf-8')).hexdigest()
    return hash

print (generate_hash(password))
```

| User Name | Nonce | Password |
| --- | --- | --- |
| user1 | 30eac1d2bdfe42de8cd8fc34c105f95c | 31bb06a1c78d0709e126686d7f5dc086d68c6b6aa10587305a4273228ada131b |
| user2 | 12c0ba5f3bb943fd81f2e9de76b0f907 | 01f8326285644388aa414922145aaeaf1bd9104f28193bbd32103799f6827a01 |
| user3 | e3155754796b4cb0824e7fdbffcc471c | 838d518e1ffb4844ac6d8d751588cf0e43b2bde0bd015c051e026dc9e0668b1e |

To check if the password is correct, we take the password from the user and the nonce and the stored digest from the database, recreate the digest and check if the recreated digest is the same as the stored digest.

```python
import uuid
import hashlib

# let us get password from the user
password="hello1234"

# let us get saved nonce and digest from the database
nonce="e3e39410b9d3481ba3c315a77b533c59"
hash_password="959595f7145ab845a0dceb476d980c4118467ef637a7178502400ba6ce5929ff"

def check(password,nonce):
    # recreate the digest
    user_hash= hashlib.sha256((password.encode('utf-8'))+nonce.encode('utf-8')).hexdigest()
    # checking the user hash with the stored hash
    if (user_hash==hash_password):
        return True
    else:
        return False

print(check(password,nonce))
```

# What is Encryption

Encryption is the process of changing plain text which is human-readable to a ciphertext that humans can't read. This is a two-way process which means when we encrypt data, we can change or decrypt it to its original form. To decrypt data we need a key, key is a random string of bits generated specifically to scramble and unscramble data.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677002643710/6bb92483-c45b-419c-a40a-537bd9e61751.jpeg align="center")

# Symmetric Key Encryption

With symmetric-key encryption, the same key is used to encrypt and decrypt the data. The simplest and least secure method of encryption is this one. A secure method of key transfer is required since the recipient needs the key to decrypt the message. The middle data can be read by anyone possessing the key.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677002266686/28efb650-495d-49a0-819b-118694fb06a8.jpeg align="center")

Python has a library `cryptography` which will help us to encrypt our data. cryptography includes both high-level recipes and low-level interfaces to common cryptographic algorithms such as symmetric ciphers, message digests, and key derivation functions. Install `cryptography` with:

```bash
pip install cryptography
```

To perform encryption and decryption of a message using the Fernet symmetric encryption algorithm. Here's the step-by-step process:

1. Import the `Fernet` class from the `cryptography.fernet` module.
    
2. Define a message string, which is "I need coffee" in this case.
    
3. Generate a random encryption key using the `generate_key()` method of the `Fernet` class.
    
4. Print the key to the console. This key will be used to both encrypt and decrypt the message.
    
5. Create an `Fernet` object using the key generated in step 3.
    
6. Use the `encrypt()` method of the `Fernet` object to encrypt the message. The `encode()` method is used to convert the message string to bytes, which is required for encryption.
    
7. Print the original message and the encrypted message to the console.
    
8. Use the `decrypt()` method of the `Fernet` objects to decrypt the encrypted message. The `decode()` method is used to convert the decrypted bytes to a string.
    
9. Print the decrypted message to the console.
    

```python
from cryptography.fernet import Fernet

message = "I need coffee"

key = Fernet.generate_key()
print(key)

fernet = Fernet(key)

encMessage = fernet.encrypt(message.encode())

print("original string: ", message)
print("encrypted string: ", encMessage)

decMessage = fernet.decrypt(encMessage).decode()

print("decrypted string: ", decMessage)
```

Note that because the encryption key is randomly generated each time the code is run, the encrypted message will be different each time.

```plaintext
Output

original string: I need coffee
encrypted string:  b'gAAAAABj9OSJfh9U2eiGTnogdjOVbCKhhceTXYkwYlDLkR_V2JouTw1hBDTgRPpKa3hGkxR4Im3GS1r0YSDhqetouD94i69lLA=='
decrypted string:  I need coffee
```

# Public Key Cryptography

Public key cryptography, also known as asymmetric cryptography, is a cryptographic system that uses two mathematically related keys – a public key and a private key – to encrypt and decrypt messages. The keys are generated in such a way that the public key can be widely distributed and shared with anyone, while the private key is kept secret and only known to the owner.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677005455952/1b7d433d-33d4-4b05-a51a-36f11272986d.jpeg align="center")

The public key is used to encrypt messages, which can then only be decrypted with the corresponding private key. This means that anyone can encrypt a message using the recipient's public key, but only the recipient with the corresponding private key can decrypt the message. In this way, public key cryptography enables secure communication between two parties who have never met or shared a secret key before.

# Secure Communication

To understand public key cryptography we need to see how we can use this concept to message someone securely in a network. Let us consider we have 4 people in the network *Green, Blue, Purple,* and *Red*. Here *Green* wants to send a message to *Blue,* so what he should do?

* Every person in the network needs to generate their own **Public Key** 🗝️ and a **Private key 🔑**. The Private Key needs to keep secret 🤫.
    
* Now, every person in the network can broadcast their public key in the network.
    
* *Green* can take *Bule’s* public key 🗝️ from the network and encrypt the message with it, which will give us a cipher text.
    
* Now, *Green* can broadcast this cipher text to the network, where every person in the network can access this encrypted text.
    
* But since the corresponding private key 🔑 is only known to Blue, only Blue can decrypt it. Any other person in the network can't decrypt it.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677090121557/305ca505-d05a-436a-83a3-4e5be8cb739a.gif align="center")

When Blue receives a message, which when he decrypts says “I Need Coffee”. How can Blue know that Green and not others sent the message?

# Digital Signatures

Blue gets the cipher text and he decrepit it with his private key but Blue does not know who sends this message in the network. He knows it was sent for him as he was able to decrepit the message.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677091825523/a5186633-17fb-4733-a52b-70280f884ac0.jpeg align="center")

> A **digital signature** is a mathematical scheme for verifying the authenticity of digital messages or documents. A valid digital signature, where the prerequisites are satisfied, gives a recipient very high confidence that the message was created by a known sender (authenticity), and that the message was not altered in transit (integrity).

This can be achieved if the message is “signed” by its sender (*Green*). The receiver of the message can then verify the signatures.

The first method we can use is to encrypt the message with Green's Private Key 🔑 so that when Blue receives the cipher text, he can decrypt it with Green's Public Key🗝️. With this, he surely knows that Green send this message to the network.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677091561039/bb0e3b0f-34a7-4bdc-8a4f-d25acdfcc94a.gif align="center")

But there is a problem when Green broadcast this message to the network everybody can decrypt this message as Green's public key is already available in the network.

Instead of signing the entire lengthy message the sender computes a hash (digest) of the message and signs that with his public key instead. The receiver can then re-compute the message hash and compare it with the signed hash to ensure that message was not tampered with.

## Adding a Digital Signature

* *Green* computes a message digest by hashing the message she is about to send. SHA256(“I Need Coffee”).
    
* *Green* calculates the message digest = HASH(message);
    
* *Green* signs the message digest by encrypting it with her private key.
    
* *Green* appends the signed digest with a message and encrypts it with *Blue's* public key *Green* sends it over to *Blue.*
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677097365003/a8b0f78b-58a6-43b6-9fc3-cc2a6a398b8e.jpeg align="center")

## Verifying a Digital Signature

* *Blue* decrypts the message using his private key
    
* *Blue* decrypts the digest using *Green's* public key
    
* *Blue* computes the digest of the message. If it matches the digest he received as signatures it confirms that:
    
    * The message is not tampered with
        
    * The message has been sent by *Green* only - Since only *Green's* public key could decrypt the hash
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677098376952/61f00381-2e7a-45a0-99a7-d661cb429868.jpeg align="center")

But wait! how could *Blue* know the public key🗝️ which he is using truly belong to *Green*? it could be *Red* pretending to be *Green*.

# Certificate Authority

In a network, there can be people who can pretend to be someone or we can say, fake people. To deal with this type of problem, we set up a **Certificate Authority**. Think of it as an Authority that is responsible for verifying our public key in the network.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677130753249/5af1069c-eda0-49e0-8e22-bb0fc01e6c1b.jpeg align="center")

## How does a Certificate Authority work?

* *Green* must contact the CA to get a certificate(digitally signed public key) to prove her public key to others. All other participants on the network will be able to trust the public key is *Green's* if they trust the CA.
    
* The CA would take *Green* through an approval/onboarding/manual verification process and issue a certificate. The certificate itself is a list of certified attributes of the entity it issued to *Green*. It has attributes like the public key, the name of the holder, etc. All this data is digitally signed by the CA using its private key.
    
* *Green* then shares this certificate as proof of his public key with *Blue*.
    
* Since *Blue* has the CA in his trusted CA list(CA’s public key), he can verify and trust the certificate shared by *Green* and hence trust her public key.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677133867358/b8528a4e-59c0-43ff-96f9-196402e5a00b.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677138121370/d5ad18a8-2965-470e-b146-ae902831f9d4.jpeg align="center")

# What's on the next article?

Next, we will see how blockchain storage work.

%%[links]