#### Challenge 1: _"The Root"_
This challenge talks about absolute paths, which are paths starting with '/'. 
Our task in this challenge is to invoke the 'pwn' program in /. 
In the terminal, I have to run /pwn and I will get the flag.

#### Challenge 2: _"Program and absolute paths"_
In this challenge, we have to execute run, which is in challenge directory, which is in /.
So the command to run would be /challenge/run

### Challenge 3: _"Position thy self"_
If we run /challenge/run in this challenge at the start, it will come up with an error message saying "you are not in the /proc/73 directory"
So I will cd to the /proc/73 directory and then run /challenge/run in that directory which will give me the flag.

### Challenge 4: _"Position elsewhere"_
Similar to challenge 3, if we run /challenge/run in this challenge at the start, it will come up with an error message saying "you are not in the /proc/69 directory"
So I will cd to the /proc/69 directory and then run /challenge/run in that directory which will give me the flag.

### Challenge 5: _"Position yet elsewhere"_
Similar to challenge 3 and 4, if we run /challenge/run in this challenge at the start, it will come up with an error message saying "you are not in the /var/lib/apt/lists directory"
So I will cd to the /var/lib/apt/lists directory and then run /challenge/run in that directory which will give me the flag.

### Challenge 6: _"implicit relative paths, from /"_
This challenge introduces us to the concept of current working directories and relative paths.

a relative path is a path that does not start with /

In this challenge, we need to run /challenge/run using a relative path with a cwd of /

the first thing i did was cd to /
and then /challenge/run using a relative path would just be to remove the / at the start, thus running challenge/run (a relative path) in / (the cwd)
this gives us the flag

### Challenge 7: _"explicit relative paths, from /"_
this challenge is similar to challenge 7, however we must run /challenge/run using an explicit relative path/

some explicit absolute paths for /challenge would be:
/./challenge
/challenge/.
/./././challenge

some explicit relative paths for challenge would be
./challenge
././challenge


here we must first cd to /
where we will run /challenge/run using an explicit relative path
so we could run ./challenge/run or ././challenge/run

challenge/run would also work however it is mentioned that we must use '.' 

not using ./ before a relative path makes it a naked path

### Challenge 8: _"Implicit relative path"_
this challenge talks about why linux avoids looking in the current directory when a naked path is provided

thus if we are in /challenge and then type run (mentioning a naked path) it will throw an error saying "run command not found"

therefore if we want to go to /challenge/run from /challenge
we must type ./run

doing this gives us the flag.

### Challenge 9: _"home sweet home"_
this challenge mentions that running /challenge/run with a file as an arguement will copy the flag into the file mentioned in arguement however the file must be no more than 3 characters long, must be in the home directory, and must be an absolute path.

after some time,  I thought could the file be '~' which is shorthand for /home/hacker. so i tried copying it into ~ and /~ both did not work. i was stuck on this problem for a while and after almost an hour i asked SENSAI for the solution which said i needed to add a file name after ~/ which should be one character long otherwise the argument would be greater than 3 chars.

so after trying ~/f, it wrote the file into home/hacker/a and then displayed the flag

