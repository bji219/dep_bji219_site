---
title:  "Vigenere Cipher"
date:   2024-04-21 15:33:33 -0500
permalink: "/VigenereCipher/"
excerpt: "62ZL.R2?VP!UTA (key: Python)"
image: assets/Images/VigenereCipher/Matrix.png
---

# Background
I read a historical fiction novel recently about the Knights Templar, and there was some reference to the [Vigenere Cipher](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher). It is an unbreakable Washington shift which utilizes a key word so that the amount of shift changes with each letter in the coded message. I was intrigued because it involves matrices, and it would be a simple and fun coding project!

![codematrix](/assets/Images/VigenereCipher/Matrix.png)

# Python Code
Here is an excerpt of the python code which reads the message to encode and the key word in order to scramble the input. 
```python
encoded = [] # Coded message initialize
count = 0 # initialize counter
for i in msg:
    r = b.index(cp[count].capitalize()) # row index from code phrase
    c = b.index(i.capitalize()) # column index from the message to be encoded

    if count == c_len-1: # reset counter if it exceeds the number of chars in the code phrase
        count = 0
    else:
        count+=1

    # The new coded letter
    nl = b[(r+c)%len(b)] # the alphabet 26 chars plus 14 punctuation chars. Modulo to get remainder
    encoded.append(nl)
    cm = ''.join(encoded)
```

# Decode 
I also created the decoding side of the equation, which would be a fun way to pass messages between friends. 
```
```
