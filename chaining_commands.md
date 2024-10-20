### Challenge 1: _"chaining with semicolons"_
here we learn that we can execute multiple commands in a single line by seperating then with a semicolon.
To get the flag we needed to run /challenge/pwn and /challenge/college together. For this we will simply run `/challenge/pwn ; /challenge/college` and get the flag

**flag: pwn.college{wUqj4udTwkkZl7xfK8Q6xavpM1g.dVTN4QDLwkjN0czW}**

### Challenge 2: _"your first shell script"_
first we need to create a "x.sh" file by writing `touch x.sh`.
Then we need to put "/challenge/pwn" and "/challenge/college" into x.sh
for this we can do `echo /challenge/pwn ; /challenge/college > x.sh`
and then we can run our shell script by running `bash x.sh`
this will give us the flag
**flag: pwn.college{8CVTEyqhCyDssysf-bBzVsoGEVH.dFzN4QDLwkjN0czW}**

### Challenge 3: _"redirecting script output"_
Here we needed to redirect output of 2 commands - /challenge/pwn and /challenge/college- into one command- /challenge/solve. For this we need to put /challenge/pwn and /challenge/college into a shell, x.sh. For this we will do `echo "/challenge/pwn; /challenge/college" > x.sh`
then run x.sh while piping the output to /challenge/solve by doing `bash x.sh | /challenge/solve`
this gives us the flag
**flag: pwn.college{A7bBcA15A1XPH2cc8f9wp-rmaG3.dhTM5QDLwkjN0czW}**

### Challenge 4: _"executable shell scripts"_
Here we needed to run a shell script without using `bash`. For this we need to make our shell file (x.sh) executable, this we can do by running `chmod uog+x x.sh` which gives the owner, groups, and all other users the permission to execute this file.
Then we can `echo /challenge/solve > x.sh` and run the shell file by simply writing the path `./x.sh`

**flag: pwn.college{8iuL-wbLoVcnAVVWzDOQVm9cFC8.dRzNyUDLwkjN0czW}**
