# GDB Baby Step 1

**Flag:** `picoCTF{549698}`

- opening the binary in gdb and seeing the assembly with 
`layout asm`
- At The End of the Function We can see in GDB that the value in hex 0x86342 is being transferred to 
eax register. 


![screenshot](assets/gdb_baby_steps.png)

- add a breakpoint at main function with `break main` 
- seen the screenshot `0x86342` is being transferred to `$eax`
- converting the value `0x86342` in decimal gives,  `549698`
- adding picoCTF{549698} to it gives the flag, 

What you learned through solving this challenge:

1.  Little bit of assembly and GDB
2.  how assembly is a topic of its own and needs a **LOT of time** 

Other incorrect methods you tried:

- Compiling and running the binary
- setting break point on `main` and trying to print the variable. 

References

- (https://www.cs.umd.edu/~srhuang/teaching/cmsc212/gdb-tutorial-handout.pdf)

---

# ARMssembly 0

**Flag:** `picoCTF{e5c69cd8}`


How you approached the challenge:

- There could have been 2 main approches to solving this problem,
    > Reverse Engineer the assmebly 
    > Compile and run the assembly like a regular program,
we are going to take the latter, because of our unfamiliarity with assembly. 

So reading the file, we have some key pieces of infomation:

```
.arch armv8-a
```
which means it is assembly for armv8.

- To compile it we need a "cross compiler" because i am currently on a x86-64 system. 
- we will also need a emulator to run the said binaries, which is qemu in this case. 

```
sudo apt install qemu-user-static && gcc-aarch64-linux-gnu
```

- now we just compile and run, 
```
aarch64-linux-gnu-as -o chall.o chall.S
aarch64-linux-gnu-gcc -static -o chall chall.o
```
compilation done now we run remember to install qemu or else it will not run. 

`./chall 3854998744 915131509 `

converting the output in hex, 

`0xe5c69cd8`

therefore as per instructions our flag will be the part without '0x' 


What you learned through solving this challenge:

1. Some basic Assembly for both x86 and arm
2. learned about gcc and the different compilers it offers. 
3. qemu emulation. 

Other incorrect methods you tried:

- Tried to read the assembly 💀💀
- spent quite a few hours trying to compile the assmebly, (the world of compilers is vast)

References:

- https://surya-dev.medium.com/armssembly-0-picoctf-8000fa11e2b0
- https://gcc.gnu.org/onlinedocs/gcc/AArch64-Options.html

