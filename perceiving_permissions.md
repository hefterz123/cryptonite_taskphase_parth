### Challenge 1: _"changing file ownership"_
here we need to use the `chown` command which stands for change owner. This can typicaly only be done by the root user however in this challenge, we the hacker user, can also use it.
First we needed to change ownership of /flag to hacker, this gives us access to do whatever root was able to do with it
once we do `chown hacker /flag` we can `cat /flag` which will read out the flag 
**flag: pwn.college{ALQRQ3y1_l1A-tuQf6Td3U1m_vf.dFTM2QDLwkjN0czW}**

### Challenge 2: _"Groups and files"_
Here we needed to change group access by using `chgrp` to the hacker group so we could get access to read the flag.
when we `chgrp hacker /flag` we has the hacker can do `cat /flag` and get the flag
**flag: pwn.college{wAwaK4cnGCLelPtqEMokSf7FVy_.dFzNyUDLwkjN0czW}**

### Challenge 3: _"fun with group names"_
Now, we could not change group access to "hacker" group, instead it was some other group that we were a part of. To find out this group name, we had to use the `id` command which would list all groups that we were part of. From this I found out that i was in grp3451. Now i simply change group access to give access to grp3451 and read the flag.
For this firstly I `chgrp grp3451 /flag` and then `cat /flag` which would read out the flag
**flag: pwn.college{EC1eKIHF-p_o8tARbM7FtH7Bv-N.dJzNyUDLwkjN0czW}**

### Challenge 4:_"changing permission"_
To change permissions of a file, we can use the `chmod` command. the `chmod` command is run with an argument which says who gets what- who+what will give 'who' the 'what' permissions, and who-what will remove 'what' permissions from 'who'
'who' could be u(user), g(group), or o(others)
'what' could be r(read), w(write), or x(execute)
this is followed by the path of the file
here we needed to change permissions of /flag so we can read it as the hacker (part of "others")
for this we will first `chmod o+r /flag` which will `ch`ange `mod`e and give `o`thers the ability to `r`ead `flag`
so now the hacker has the ability to read the flag and `cat /flag` will give us the flag EZ
**flag: pwn.college{I2ruDkkEUGo3GKc-ugFuR3zBwEh.dNzNyUDLwkjN0czW}**

### Challenge 5: _"Executable files"_
Here we need to change the files permissions so we can execute it as the hacker.
the program `/challenge/run` must be executable by the hacker
so first i `chmod o+x /challenge/run` to give others the permission to execute `/challenge/run` but this showed "permission denied"
This was because hacker is not in "other" this time, it is the user
So we needed to do `chmod u+x /challenge/run` and then run `/challenge/run` to get the flag.
Initially, after the first problem, i gave everyone permission to do everything by running `chmod oug+rwx /challenge/run` which worked, but when i gave permissions individually, i found out that hacker is the user here.

### Challenge 6: _"Permission tweaking practice_"
Here there were 8 different tasks, changing permissions again and again. After solving all 8 correctly in a row, we got access to tweak permissions of `/flag`.
So we `chmod ugo+r /flag` giving everyone permission to read the flag and then we `cat /flag` to get the flag
**flag:pwn.college{A3b-Jo5CutxcYVH1G_T8e5sHwAB.dBTM2QDLwkjN0czW}**

### Challenge 7: _"Permissions setting practice_"
Here we can set the permissions for user,group, and other seperately by using `chmod who=what`. For example `chmod u=rwx` will give user the permission to read,write, and execute. You can also set permission for all of them in a single line by seperating it with a ','. For example `chmod u=wx,g=r,o=-` will give user the permission to write and execute, group the permission to read, and no permission for others.

We had to set permissions for /challenge/pwn 8 times before we had access to change permission of /flag. After we got access to change permissions of /flag, we can give read permission to user hacker by running `chmod u+r /flag` and then `cat /flag` to get the flag
**flag: pwn.college{cNI5eX3oYV-0KD047ftqHe0R15w.dNTM5QDLwkjN0czW}**

### Challenge 8: _"The SUID bit"_
here we learn how to set a files "Set User ID". Running the SUID means that no matter which user ran the program, it will always run as if they owner ran it.
Here we had to set SUID for /challenge/getroot by running `chmod u+s /challenge/getroot` Then on running /challenge/getroot, it would run as if they owner ran it, and this would put us in the root shell. Here we can run `cat /flag` and get the flag
**flag: pwn.college{Q8U48xr0rGoDiqHe5NGFO3F8UOO.dNTM2QDLwkjN0czW}**
