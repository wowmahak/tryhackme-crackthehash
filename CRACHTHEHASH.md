# [WALKTHROUGH]TRYHACKME ROOM: crackthehash
[ACCESS ROOM HERE](https://tryhackme.com/r/room/crackthehash)

## AIM:
To seamlessly walk you through the “Crack the hash” practice room in TRYHACKME.

## TOOLS REQUIRED:
+ [Crackstation](https://crackstation.net) to crack non-salted passwords {specifically MD5, MD4, SHA-1, SHA-256, SHA-512}[Level1]
+ [Hash Analyzer](https://hashes.com/en/tools/hash_identifier) to identify the hash type[Level1&2]
+ [MD4 Hash Cracker](https://www.dcode.fr/md4-hash) to specifically crack the MD4 hashes[Level1]
+ [MD5 Hash Cracker](https://md5decrypt.net/en/) to specifically crack the MD5 hashes[Level1]
+ [Hash Formats](https://hashcat.net/wiki/doku.php?id=example_hashes) List by hashcat[Level1&2]
+ Hashcat to be installed on your computer[Level1&2]
+ rockyou password list text file{its a leaked commonly used password list which we will be using for the dictionary attack through hashcat as a reference wordlist}You can download this online.
> Note:
You are advised to copy and paste all the hashed passwords into a text file and name it as “hashedpass.txt”

## Level-1{Use Online tools}


### Hash-1.1) 48bb6e862e54f2a795ffc4e541caed4d

> To crack this hash, you can copy this and then, paste it on the crackstation. On clearing up the reCAPTCHA, hit on “crack hashes” and it will provide the answer.

### Answer-1.1) easy


### Hash-1.2) CBFDAC6008F9CAB4083784CBD1874F76618D2A97

> To crack this hash the above process follows same, you can copy this and then, paste it on the crackstation. Clearing up the reCAPTCHA, hit on “crack hashes” and it will provide the answer in a table format; in the “result” section is our required answer.

### Answer-1.2) password123


### Hash1.3)1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032

> To crack this hash the above process follows same, you can copy this and then, paste it on the crackstation. Clearing up the reCAPTCHA, hit on “crack hashes” and it will provide the answer in a table format; in the “result” section is our required answer.

### Answer-1.3) letmein


### Hash-1.4) $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom

> To crack this password, unfortunately one cannot use the crackstation. You may ask, why?? and the answer is: Its uses “bcrypt” algorithm(You can check this by pasting the hash in the above linked hash analyzer and hitting “analyze” button!) which crackstation unfortunately cannot crack on! So, here we have to take the long way of using “THE HASHCAT”.
Head to the terminal and type the following code:

```hashcat -a0 -m3200 hashedpass.txt rockyou.txt```

>Here:
> + a stands for “attack” which is followed by a “0” which means that its going to be a dictionary attack.
> + m stands for “attack-mode” which is followed by 3200 means that the hash type is bcrypt(You can see the attack mode from the hash formats list provided above.
> On hitting enter, you will sadly be prompted to wait for a while and BOOM!!!!!!!…The password is here!!!!

### Answer-1.4) bleh


### Hash-1.5) 279412f945939ba78ce0758d3fd83daa

> To crack this hash, you can copy this and then, paste it on the crackstation. Clearing up the reCAPTCHA, hit on “crack hashes” and it will provide the answer in a table format; in the “result” section is our required answer.

### Answer-1.5) Eternity22

## LEVEL-2 {USING HASHCAT}


### Hash-2.1) F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85
You first need to look up for the hash type in the above linked hash analyzer and on hitting the “Submit and Continue” button, you will find that the hash type is “SHA2–256”. Hence, open the terminal and hit the below command:

```hashcat -a0 -m1400 hashedpass.txt rockyou.txt```

> You can check the attack mode from the above linked “Hash Formats List” and from there, you will find out that the required is “1400”.
On hitting enter, and after waiting up for some time, you get your answer!

### Answer-2.1) paule


### Hash-2.2) 1DFECA0C002AE40B8619ECF94819CC1B

You first need to look up for the hash type in the above linked hash analyzer and on hitting the “Submit and Continue” button, you will find that the hash type is “NTLM”. Hence, open the terminal and hit the below command:

```hashcat -a0 -m1000 hashedpass.txt rockyou.txt```

> You can check the attack mode from the above linked “Hash Formats List” and from there, you will find out that the required is “1000”.
On hitting enter, and after waiting up for some time, you get your answer!

### Answer-2.2) n63umy8lkf4i


### Hash2.3)$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02with Salt: aReallyHardSalt

> You first need to look up for the hash type in the above linked hash analyzer and on hitting the “Submit and Continue” button, you will find that the hash type is “sha512crypt $6$, SHA512 (Unix) 2”. Hence, open the terminal and hit the below command:

```hashcat -a0 -m1800 hashedpass.txt rockyou.txt```

> You can check the attack mode from the above linked “Hash Formats List” and from there, you will find out that the required is “1800”.
On hitting enter, and after waiting up for some time, you get your answer!

### Answer-2.3) waka99


### Hash-2.4) e5d8870e5bdd26602cab8dbe07a942c8669e56d6

> You first need to look up for the hash type in the above linked hash analyzer and on hitting the “Submit and Continue” button, you will find that the hash type is “SHA-1”. But, since the hash is salted, one cannot use “100” as the attack-mode, so, one needs to try the salted passwords version of hash type. On trying, you will find out that the required attack mode will be “160”. Hence, the required command will be:

```hashcat -a0 -m160 hashedpass.txt rockyou.txt```

> On hitting enter, and after waiting up for some time, you get your answer!

### Answer-2.4) 481616481616



