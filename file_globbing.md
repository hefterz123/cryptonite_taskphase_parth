### Challenge 1: _"matching with *"_
here we learn about the * glob
so basically when the system encounters * it will fill the * with any file which follows the pattern before or after the *
e.g. we have 3 files: abc1 abc2 abc3
if we do ls abc*, it will list all files starting with abc - abc1 abc2 abc3

so here we need to go to challenge directory from home directory using * glob and the argument must not be more than 4 characters.
So I run cd /ch* which takes me to /challenge
there we run /challenge/run and get the flag
**flag: pwn.college{oMndeudZZEQ2l3tGxXiXYsmcJQD.dFjM4QDLwkjN0czW}**

### Challenge 2: _"matching with ?"_
the second glob we learn about is ?
which does similar things as * except here we have to specify how many unknown characters are there
e.g. let there be 3 files- abc1 abc2 abc123
ls abc* would list all 3, abc1, abc2, and abc123
but ls abc? would only list abc1 and abc2 because there is only one question mark after abc which means we want files with only one character after abc

so here to go to /challenge, it is mentioned replace c and l with ?
so we run cd /?ha??enge which takes us to /challenge
there we run /challenge/run and get the flag
**flag:pwn.college{cAIg8ZogLIh0w6DRJL4TWZJrPEv.dJjM4QDLwkjN0czW}**

### Challenge 3:_"matching with []"_
the third glob is []. Here we have to specify potential characters to match with the file, in the square brackets.
e.g. let there be 3 files- abc1 abc2 abc123
ls abc[3] would only match with files with 3 in it- so abc123
ls abc[1] would match with abc1 and abc123
ls abc[2] would match with abc2 and abc123

here we had to go to /challenge/files and run /challenge/run with an argument that would bracket-glob with all these files: file_a file_b file_s and file_h

so we run /challenge/run file_[absh] and this gives us the flag

**flag: pwn.college{sxNBaoXCTwbMRk6BE9_WKCjlTBh.dNjM4QDLwkjN0czW}**

### Challenge 4: _"matching paths with []"_
here we specify the path of the files and glob in the path
for example, the files, file_a file_b file_s and file_h, in /challenge/files, would be globbed as /challenge/files/file_[absh]
we run this file path as an argument in /challenge/run to get the flag

so we run /challenge/run /challenge/run/file_[absh] and this gives us the flag

**flag: pwn.college{AJLxW8M7-W0hOGFzKul9x94eBQN.dRjM4QDLwkjN0czW}**

### Challenge 5: _"mixing globs"_
here we have to match the files "challenging", "educational", and "pwning" using an argument, no more than 6 characters, in /challenge/files

we can type ls [cep]* and see what files match. This would match all files beginning with c, e, or p. Fortunately, in this case, each file begins with a different letter

so [cep]* matches only to the files we want. So /challenge/run [cep]* will give us the flag
**flag: pwn.college{osXOi_acgjKqVZND4LX0Kcyqk2j.dVjM4QDLwkjN0czW}**

### Challenge 6: _"exclusionary globbing"_
here we learn about using ! or ^ inside []. So [abc]* will show us all the files which **start** with a,b,or c. BUT [!abc]* whill show us all the files that **do not** start with a,b, or c

here we needed to see the files that dont start with p,w,n in /challenge/files
so in /challenge/files, we will run /challenge/run [!pwn]* which will expand to all files that dont start with p,w, or n. This gives us the flag 
**flag: pwn.college{EpawLnjtuXlBaFdikGe_MZi3kxU.dZjM4QDLwkjN0czW}**

