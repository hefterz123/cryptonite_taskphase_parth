### Challenge 1: _"the PATH variable"_
when we run `PATH=""` and then write a command such as `ls` or `rm` it will show "no such file or directory" because shell cannot run `ls` or `rm` without a path.
Here we needed to remove `rm` and then run `/challenge/run`, otherwise if we run `/challenge/run` without removing `rm` it would remove the flag.
For this we will simply `PATH=""` and then run `/challenge/flag` which will give us the flag because the shell is not able to find the path to `rm`

**flag: pwn.college{cmL77-_FPSdJKLo-oGMZtVV05hl.dZzNwUDLwkjN0czW}**

### Challenge 2: _"setting PATH"_
To do someting useful with `PATH`, we can set a path to it which can invoke other scripts.
normally to invoke a script, we would need to mention the entire path of it, but if we add the path of the script to `PATH` then we can invoke it by its bare name.
Here we needed to invoke `win` by its bare name which is in the /challenge/more_commands directory. So we will first add that path by `PATH=/challenge/more_commands/` and then `/challenge/run` will invoke `win` by its bare name and give us the flag.

**flag: pwn.college{QxR8Oxyzz_UllTUxPwLvsrfr8Rv.dVzNyUDLwkjN0czW}**

### Challenge 3: _"adding commands"_
first we needed to create a shell file called "win" in a directory, "cmd". This cant be win.sh or else the program would not run, so to make it function as a shell file we need to `echo #!/bin/bas > ~/cmd/win`. I realised this with the help on sensAI.
after that we can `echo cat /flag >> win` and then make sure win is executable by `chmod uog+x ~/cmd/win`
then we have to set the path so we can use win as a command, we can do this by `PATH=~/cmd/:$PATH`. this puts ~/cmd/ first, and then $PATH, which is just the current path including `cat` and `ls`. If we only type `PATH=~/cmd/` then `cat` would not work, in that case we would need to `echo read /flag > win` instead.
After all this is done we can `/challenge/run` and get the flag

**flag: pwn.college{g2_7pk84r6-HWUe-321WFWjJ6vx.dZzNyUDLwkjN0czW}**


### Challenge 4: _"Hijacking commands"_
Here we needed to create a new rm file which does something else instead of deleting. Here after `/challenge/run` the program would search for `rm` and execute it. So instead we can create a new `rm` in a directory "cmd" which can `cat /flag` by typing `echo cat /flag > ~/cmd/rm`.
Make sure the new `rm` is executable by `chmod uog+x rm`. Then we can change the path to include our new rm, make sure this path comes before the path to actual `rm` so that the deleting rn does not get executed first.

After `PATH=~/cmd/:$PATH` we can `/challenge/run` which will find `rm` and execute it. Since our rm comes before the actual rm, our rm is executed first which will print out the flag

**flag: pwn.college{AU4vrXcVMqyguthMRNse4314gFZ.ddzNyUDLwkjN0czW}**
