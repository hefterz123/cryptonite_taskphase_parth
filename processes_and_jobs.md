### Challenge 1: _"Listing processes"_
In this challenge we learn about `ps` command (program status) and using `ps -ef` (e-every program; f-full format) or `ps aux`(a-all users; u-user readable; x-show the programs not in terminal) to display list of running programms.
Here /challenge/run was renamed to something else which was running, we had to list all running programs to figure out which one was the new /challenge/run and rerun it to get the flag
first i did `ps aux` which gave me the list of all running programs, there i found a program called /challenge/20365-run-18414.
Upon running /challenge/20365-run-18414, i got the flag.
**flag: pwn.college{Q1GUs7j_q0GmHtQy4KjqT3x-BhX.dhzM4QDLwkjN0czW}**

### Challenge 2: _"Killing processes"_
Here we learn to use the `kill` command to terminate a program
We needed to terminate a program /challenge/dont_run and then run /challenge/run to get the flag.
First i did `ps aux` to get the PID of /challenge/dont_run which was 73
then i did `kill 73` which terminated the program and then i ran /challenge/run which gave me the flag
**flag: pwn.college{UzJmA5To6L1duYdjZDPUUQs3zhm.dJDN4QDLwkjN0czW}**

### Challenge 3: _"Interrupting processes"_
To interrupt a process, we need to press `CTRL+C` on our keyboard. This is the hotkey to interrupt a process which is currently waiting for an input. This would exit the process.
We needed to run /challenge/run and then interrupt it by pressining CTRL+C
this gave us the flag
**flag: pwn.college{c2vp1ry8uv_37DUAThZPowX2Ffv.dNDN4QDLwkjN0czW}**

### Challenge 4: _"Suspending processes"_
To suspend processes to the background, without stopping them completely, can be done by pressing `CTRL+Z`. 
Here we needed to suspend /challenge/run and while it was suspended, we needed to run /challenge/run again which would create a copy of /challenge/run when we do `ps aux`
If the system sees a copy of /challenge/run, it will give us the flag
**flag: pwn.college{Y4dOABrMT8-5hqiYHLcj6jvTcjX.dVDN4QDLwkjN0czW}**

### Challenge 5: _"Resuming processes"_
We can resume the suspended processes by typing `fg` (foreground) and passing the process as an argument.
Here we first needed to suspend /challenge/run and then resume it.
So firstly we run /challenge/run and then press `CTRL+Z` to suspend it and then type `fg /challenge/run` to resume it. This gives us the flag
**flag: pwn.college{coDc9HJus_DNG-CZwCrjGZYX0h1.dZDN4QDLwkjN0czW}**

### Challenge 6: _"Backgrounding processes"_
So the `fg` command is used to run processes in the foreground, similarly there is a `bg` command which runs program in the background. This allows the program to run while your shell is available for you to run more commands.
We needed to run a copy of /challenge/run in the backgroud and run it again foreground to get the flag.
(in the STAT column in `ps aux` T means the program is suspended, R means it is running in the background, and R+ means it is running in the foreground. However if we run `bg sleep cmd-name` to the command which was originally suspended, the T changes to a S, which means it is sleeping, not suspended)

Anyways, to get the flag, we first need to run /challenge/run, then suspend it by pressing `CTRL+Z` then resume it in the background using `bg /challenge/run` and then run it again in the foreground by using `/challenge/run`. This creates a copy, one in background and one in foreground, both running. This gives us the flag
**flag: pwn.college{4Op-QKRCens1zwwRvMIK9bV-FG7.ddDN4QDLwkjN0czW}**

### Challenge 7: _"Foregrounding processes"_
This teaches us we can use the `fg` command to foreground a background process without re-suspending it, simply by running `fg cmd-name` while the command is running in the background
In this challenge, we needed to run /challenge/run `/challenge/run`, suspend it `CTRL+Z`, run it in the background `bg /challenge/run`, then bring it to the foreground without resuspending it `fg /challenge/run`.
This gives us the flag
**flag: pwn.college{cJlE7Nf0uK_tKcGj2LRtvYLaxYK.dhDN4QDLwkjN0czW}**

### Challenge 8: _"Starting backgrounded processes"_
Earlier, we had to run a program, suspend it, and then type `bg cmd-name` to run it in the background. 
A simpler way would be to run the command and add an '&' to the end of it, such as `cmd-name &` this would directly run the command in the background
We need to run /challenge/run in the background directly to get the flag. So simply `/challenge/run &` would give us the flag
**flag: pwn.college{EFhGzS3QSi_p7emYgjxw9ZWID3m.dlDN4QDLwkjN0czW}**

### Challenge 9: _"Process Exit Codes"_
Every command that terminates has an exit code, this can be accessed by using `?` and displayed by using a `$` before it, so like `echo $?` to get the exit code.
Here we needed to run /challenge/get-code, get the exit code, and run /challenge/submit-code with the exit code as an argument.
`/challenge/get-code`
`echo $?` _this gave the output 111_
`/challenge/submit-code 111`
this gave us the flag
**flag: pwn.college{4xhg0w501WyxprcHQKQTdYL5Bj0.dljN4UDLwkjN0czW}**


