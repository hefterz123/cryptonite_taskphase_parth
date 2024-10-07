### Challenge 1: _"cat: not the pet, but the command"_
here the flag file was copied into my home directory
if we type ls when the current working directory is ~ then we could see the flag file.
on typing cat flag, the flag was displayed

### Challenge 2: _"catting absolute paths"_
here we had to add an absolute path as the argument for the cat command.
upon typing cat /flag, the flag was visible

### Challenge 3: _"more catting practice"_
in this challenge, there was no flag file in the home directory, it was in /lib/jvm/default-java and using cd was not allowed. since we can type absolute paths as arguments, the solution would be to type "cat /lib/jvm/default-java/flag".

### Challenge 4: _"grepping for a needle in a haystack"_
the grep command is used to search for a particular string in a file. it was mentioned that the flag is in /challenge/data.txt with many other words so to search for the flag use the grep command and the flags always start with "pwn.college"
on doing grep pwn.college /challenge/data.txt we get the flag

### Challenge 5: _"listing files"_
here we had to use ls command to see all the files in /challenge because 'run' had been renamed to something else. upon doing ls /challenge we see that "run" was renamed to "11980-renamed-run-23245"
so instead of doing /challenge/run to get the flag, we had to do /challenge/11980-renamed-run-23245 to get the flag.

### Challenge 6: _"touching files"_
in this _freaky_ challenge, we need to create files using the touch command.
we need to create 2 files, "pwn" and "college", in /tmp by typing touch /tmp/pwn and touch /tmp/college 
this gets us the flag.

### Challenge 7: _"removing files"_
in this challenge we needed to remove the delete_me file by simply typing rm delete_me
after this we run /challenge/check to get the flag.

### Challenge 8: _"hidden files"_
when we type ls, it does not show all files, all files prepended by a '.' are hidden in ls. To see these files we need to type "ls -a"

in this challenge, the flag is a dot-prepended file which can only be seen by typing ls -a
after doing this we can see the flag is in a file called flag-118711977356, which we can read by doing cat flag-118711977356

### Challenge 9: _"An Epic Filesystem Quest"_
First off, the given hint was that our first hint is in /
There was a file called MESSAGE, cat MESSAGE gave us another hint saying "The next clue is in: /usr/local/lib/python3.8/dist-packages/numpy/random/_examples" and the next clue is a hidden file, it starts with a '.'character

then we cd to /usr/local/lib/python3.8/dist-packages/numpy/random/_examples, and then we have to type ls -a to see the hidden file. we can see a file called .INFO. on doing cat .INFO we got our next directory to go to.

in the next directory, upon doing ls, we found a file called DEMO, doing cat DEMO gave us the next directory, and also said the next file is hidden.

on going to the next directory, we must do ls -a to see the hidden file, called .WHISPER. on doing cat .WHISPER, we got the next hint with the next directory and it also mentionede that we cannot cd to this directory or it will self destruct.

so we must see the files in this directory by giving it as an arguement to ls
 "ls /usr/share/icons/hicolor/64x64/emotes" would list the files, where there was a file called README_TRAPPED, so we would simply type cat  ls /usr/share/icons/hicolor/64x64/emotes/README_TRAPPED to read this file which would give us the next hint.
 
 next hint was that we would not be able to see the file until we 'cd' into that directory. which means ls /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/STIX/IntegralsSm would not show us anything. on cd'ing to that directory and doing ls we found a file, cat that file and we got the next hint
 
 the next few hints had the same process as the previous one, and eventually we got the flag.
 
 ### Challenge 10: _"making directories'_
 we can make directories using the mkdir command.
 here we can do make a directory /tmp/pwn  and make a file called college in it
 first we do mkdir /tmp/pwn and then we do touch /tmp/pwn/college. after this we get the flag by running /challenge/run
 
 ### Challenge 11: _"finding files"_
 we have to use the find command in this challenge. to find a file in / named flag
 we have to type "find / -name flag"
 we will get a bunch of files called flag, we must try to read all of them and one of them will have the flag we are looking for.
 
 
 ### Challenge 12: _"linking files"_
 here we learn about hard and soft links, and creating symlinks between 2 files
 if we run /challenge/catflag it will read out /home/hacker/not-the-flag.
 since i knew the flag is stored in /flag and i had to create a symlink between /flag and some other directory, i tried making a symlink to firstly ~/not-the-flag and then ran cat ~/not-the-flag which did not work. So after that i tried creating a symlink to /challenge/catflag which also did not work. After taking some help from SENSAI, i realised my first step was correct, to create a symlink to ~/not-the-flag however to get the flag, i had to run /challenge/catflag instead of cat ~/not-the-flag
 this gave me the flag

 
