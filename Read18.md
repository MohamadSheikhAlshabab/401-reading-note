# Readings: Cryptography [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read18.md)

## Caesar cipher:
  - In cryptography, a Caesar cipher, also known as Caesar's cipher, the shift cipher, Caesar's code or Caesar shift, is one of the simplest and most widely known encryption techniques. 
  -  It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
  - Example:
    - `Plain:    ABCDEFGHIJKLMNOPQRSTUVWXYZ`
    - `Cipher:   XYZABCDEFGHIJKLMNOPQRSTUVW`
  - Breaking the cipher:
    -  Two situations can be considered:
      - 1 - an attacker knows (or guesses) that some sort of simple substitution cipher has been used, but not specifically that it is a Caesar scheme: such as frequency analysis or pattern words.
      - 2 - an attacker knows that a Caesar cipher is in use, but does not know the shift value: One way to do this is to write out a snippet of the ciphertext in a table of all possible shifts known as "completing the plain component".
        - Since there are only a limited number of possible shifts (25 in English), they can each be tested in turn in a brute force attack.
        - ex: 
  
| Decryption shift|	Candidate plaintext |
| ---             | ---	                |
|0	              |>exxegoexsrgi        |
|1	              |dwwdfndwrqfh         |
|2	              |cvvcemcvqpeg         |
|3	              |buubdlbupodf         |
|4	              |attackatonce         |
|5	              |zsszbjzsnmbd         |
|6	              |yrryaiyrmlac         |
|... 	            |                     |
|23	              |	haahjrhavujl        |
|24	              |	gzzgiqgzutik        |
|25 	            |	fyyfhpfytshj        |

---
## Cryptography: Crash Course Computer Science #33:
  - __defence in depth__: is system architects employ stratgy which uses many layers of varing security mechanisms to frustrate attackers.
  - __Cryptography__: roughly translating to "secret writing".
  - __cipher__: is an algorithm that converts plain text to ciphertext, which is gribberish unless you have a key that lets you undo the cipher.
  - __encryption__: is the process of making text secret, and the reverse process called __decryption__.
  - To decipher a message, recipients had to know both the algorithm and the number to shift by which acted as the key.
  - __substitution cippher__: is replace every letter in the message with something else according to a translation.
  - __cryptanalyst__: develops mathematical methods and codes that protect data from computer hackers.  
  - __permutation cipher__:  a permutation cipher is a transposition cipher in which the key is a permutation.
  - DATA ENCRYPTION STANDARD (DES) used keys that were 56 bits long, which means that are 2 to 56 or about 72 quadrillion different keys (72 with 15 zeros).
  - ADVANCED ENCRYPTION STANDARD (AES) use much keys - 128, 192 or 256 bits in size - making brute force attacks much, much harder.
  - for a 128 bit keys you need trillions of years to try every combination.
  - AES used everywhere from encrypting files, transmitting data over WIFI with WPA2, and to accessing websites using HTTPS.
  - __key exchange__: is an algorithm that lets two computers agree on a key without ever sending one using one-way function.
  - The Caesar cipher, AES and Enigma are all symmetric encryption.
  - asymmetric encryption: is use two diiferent keys, the one is public and the second is private. the public use to encrypt and the private use to decrypt.
  
  
  
  - 
  
  
  
