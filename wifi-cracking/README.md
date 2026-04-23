Wi-Fi Security & Password Cracking
Subject: Cryptography  UTS
Tools Used: Aircrack-ng, Wireshark, Linux CLI 
Topics: AES Encryption, WEP/WPA2/WPA3, Four-Way Handshake, Wireless Attack Techniques

Overview
This lab had two parts: understanding how AES encryption works under the hood, and then getting hands-on with real wireless security vulnerabilities by cracking WEP and WPA2 passwords using Aircrack-ng. 
It's one thing to read about why WEP is broken; it's another to actually crack it and see the password appear on your screen.

What I Did
Task 1Visualising AES Encryption
Stepped through AES encryption round by comparing plaintext against the output after Round 1, and then the final encrypted output. Used an AES animation tool to visualise how the substitution, shifting,
and mixing operations transform the data across each round. This gave a much clearer picture of why AES is so hard to reverse without the key.
Task 2 Cracking Wi-Fi Passwords
WEP Cracking (PTW Mode) Used Aircrack-ng in PTW mode to crack a WEP password. PTW is particularly efficient because it only needs around 20,000–40,000 captured packets 
to statistically recover the key, much fewer than older methods.
WEP Cracking (Korek Mode) Repeated the attack using Korek mode, which requires more packets but uses a different statistical approach. Comparing the two methods 
highlighted how WEP's fundamental design flawIV reusemakes both attacks possible regardless of the method used.
WPA2 Cracking Captured the WPA2 four-way handshake and ran a dictionary attack against it. The handshake is captured passively (or by deauthenticating a client to 
force a reconnect) and then cracked offline meaning the attack doesn't interact with the access point at all after capture.

Key Findings
Why WEP is broken: WEP reuses Initialisation Vectors (IVs) across packets and uses a weak CRC-32 integrity check. These two flaws together make it trivially crackable
with enough captured traffic and tools like Aircrack-ng make collecting that traffic very fast.
WPA2's weakness: The KRACK (Key Reinstallation Attack) vulnerability allows attackers to potentially decrypt traffic by manipulating the four-way handshake. 
While patches exist, unpatched devices remain vulnerable. Dictionary attacks against captured handshakes are also highly effective if weak passwords are used.
WPA3 improvements: WPA3 addresses WPA2's shortcomings with GCMP-256 encryption (vs 128-bit), the Dragonfly handshake which prevents offline dictionary attacks, 
and forward secrecy so past sessions can't be decrypted even if the password is later compromised.

Key Takeaways
WEP should never be usedit's not just outdated, it's fundamentally broken at the design level
WPA2 is safe with strong, unique passwords dictionary attacks only work when passwords are weak
WPA3 is the current gold standard but limited device support creates security gaps in mixed networks
Understanding how these attacks work is essential for anyone configuring or auditing wireless networks

Skills Demonstrated
Aircrack-ng, WEP/WPA2/WPA3, Wireless Security, AES Encryption, Four-Way Handshake, Dictionary Attacks, Network Security Auditing, Linux CLI.

