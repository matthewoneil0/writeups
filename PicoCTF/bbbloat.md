# bbbloat
**Description**: Can you get the flag? Reverse engineer this [binary](https://artifacts.picoctf.net/c/302/bbbbloat).

Not given much right? To start this one off I gave executible permissions to myself on the file and run it to see what happens. Below you can see we get a simple question program.

![progam1](/imgs/bbbloat1.png)

Now time to open up the binary in Ghidra and take a look around. After looking at the entry function, it leads me to a function that prints the messages to the screen. We also notice that, in the same function, the program compares a variable with a space in memory.

![Ghidra](/imgs/bbbloat2.png)

Here I changed the function name to 'checkNumber', renamed the integer we are comparing to 'input', as well as wrote precomments to make it more readable. 

Knowing this. My next thought is to run the program in gdb and examine 0x86187 in memory after running the program.

![program2](/imgs/bbbloat3.png)

I only use the *run* command here to run the program, and then the *print* command with the specific memory address to print the value of it. 

Now let's try entering 549255 into the program as the favorite number. 

![final](/imgs/bbbloat4.png)

And there you have it. The flag is `picoCTF{cu7_7h3_bl047_695036e3}