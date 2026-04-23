Block Cipher Operations
Subject: Cryptography (42000)  UTS
Tools Used: OpenSSL, Bless (Hex Editor), Linux CLI
Topics: Cipher Modes, ECB vs CBC, Padding, IV Analysis, Error Propagation

Overview
This lab went deep into how block ciphers actually behave in practice, not just what the textbook says, but what happens when you encrypt real files with different modes and then look 
at the output. The most revealing part was encrypting an image with ECB vs CBC and seeing with your own eyes why ECB is considered broken for most use cases.

What I Did
Task 1  Encrypting with Different Cipher Modes
Used OpenSSL to encrypt files using three different cipher modes  AES-128-CBC, AES-128-CFB, and Blowfish-CBC. Compare the resulting ciphertext outputs to understand 
how each mode handles data differently at the block level.

Task 2  ECB vs CBC: The Image Test
This was the most visually striking part of the lab. Encrypted a .bmp image file using both AES-128-ECB and AES-128-CBC, then recovered the image structure by replacing only 
the encrypted body while keeping the original header.
ECB result: The grayscale outline of the original image was still clearly visible in the encrypted file. Because ECB encrypts each block independently, identical pixel blocks 
produce identical ciphertext blocks  and the pattern leaks through.
CBC result: The recovered image was completely gray with no recognisable structure. CBC chains each block to the previous one, so identical input blocks produce completely 
different outputs.
This is not just a theoretical weakness, it's a visual demonstration of why ECB mode should never be used to encrypt structured or repetitive data.

Task 3  Padding
Encrypted files of different sizes and used the -nopad flag during decryption to expose the raw PKCS#7 padding that OpenSSL adds. Viewed the hex representation using 
Bless to confirm exactly how many padding bytes were added and what their values were.

Task 4  Error Propagation
Intentionally corrupted a byte in a ciphertext file using Bless, then decrypted it to observe how the corruption propagated through each cipher mode. 
Different modes have very different error propagation characteristics: ECB confines corruption to a single block, while CBC corrupts two blocks, 
and stream-like modes (CFB, OFB, CTR) handle corruption differently again.

Task 5  Initialisation Vector (IV) Behaviour
Encrypted the same plaintext file multiple times using different IVs and observed the resulting ciphertexts. Confirmed that even with the same key, 
a different IV produces completely different ciphertext  which is why IVs must be unique and unpredictable for every encryption operation.

Key Takeaways
ECB mode leaks structural information about the plaintext  never use it for anything beyond single-block data
CBC is significantly more secure than ECB but requires a unique, unpredictable IV for every encryption
Padding is a necessary part of block cipher operation  understanding it matters for avoiding padding oracle attacks
Error propagation behaviour varies significantly between modes and is an important factor in choosing the right mode for a given application

Skills Demonstrated
OpenSSL, AES Encryption, Block Cipher Modes (ECB/CBC/CFB/OFB/CTR), Hex Analysis, IV Management, Padding, Error Propagation, Linux CLI

