# C3
**Flag:** `picoCTF{adlibs}`

- We have the Code used to encrypt the original cipher text, spent long time on trying to understand what it was doing,

```
import sys
chars = ""
from fileinput import input
for line in input():
    # print(line)
    chars += line
# print(chars)

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0

for char in chars:
  # print(char)
  cur =  lookup2.index(char)
  nigga = (cur + prev) % 40
  out += lookup1[nigga]
  prev = nigga
    

sys.stdout.write(out)

```
The above code will Decrypt the given cipher text, save the file to `reverse_datshit.py` and run  `python3 reverse_datshit.py ciphertext > solve1.txt`


```
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1

```

- this is the decoded cipher text, the comments suggest it that it is python2 code but with trivial changes it can be converted to python3 code. 


```
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 

for i in range(len(chars)):
    if i == b * b * b:
        print(chars[i], end='') #prints
        b += 1 
```
- beyond this i was a little confused as to what to give it input, 
- i then gave the code file itself (solve1.txt) as input and got the word `adlibs` i added  the `picoCTF` to it and voila !! it worked. 

- 
![screenshot](assets/c3.png)

What you learned through solving this challenge:

1. Reverse Things in general specially the Modulo function 
2. Patience, (a lot of it !!)

Other incorrect methods you tried:

- Incorrectly Reversing the file over several Hours trying out different things
- not Reading the entire prompt and wondering what went wrong even when at the end i had succefully completed the problem, 




References

- https://stackoverflow.com/questions/10133194/reverse-modulus-operator sup sathvick
- https://www.geeksforgeeks.org/python-sys-module/ pretty cool if you actually read till here