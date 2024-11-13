# Trivial Flag Transfer Protocol

**Flag:** `picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}`

The name of the challenge Implies that it has got something to do with  TFTP (trivial file transfer protocol):

- Download pcapng file and open it in wireShark, 
- We see several tftp reqs the first one has a string,
```
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
```
Decoding that with ceaser cipher with a shift of 13 gives

```
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```

Oh huh, assuming that there are more files we do a EXPORT-objects with tftp in wire-shark, 
this gives us all the files transfered with the network 
and we see the follwing files
![screenshot](assets/all_files_wireshark.png) 

- do a  `cat plan` and decode with ROT13 gives,   
```
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```
The Emphasis on DueDiligence interesting ;),

- the program.deb is the deb file of a program called steghide, which is used to hide data inside images, 
- THe flag is probably hidden inside the images with steghide with pass... (DUEDILIGENCE)??

`steghide extract -sf ./picture1.bmp `
`steghide extract -sf ./picture2.bmp `
`steghide extract -sf ./picture3.bmp`

in the third file we get, 
```
steghide extract -sf ./picture3.bmp 
Enter passphrase: 
wrote extracted data to "flag.txt".
```

What you learned through solving this challenge:

1. Little Bit of WireShark
2. StegHide
3. small bits about tftp

Other incorrect methods you tried:

- Tried to search for the flag by `strings | grep pico` 
incorrectly assuming that the flag mightbe directly embedded in some request. 

References

- https://steghide.sourceforge.net/documentation/manpage.php
- https://www.geeksforgeeks.org/what-is-tftp-trivial-file-transfer-protocol/
