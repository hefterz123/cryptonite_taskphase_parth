### Challenge 1: _"Learning From Documentation"_
in this challenge, a docuementation was given about the program /challenge/challenge where it mentioned we had to run it with an argument of --giveflag
on typing /challenge/challenge --giveflag we got the flag 
pwn.college{QykUJgsS5rXFxSAD6IEY09-KEgE.dRjM5QDLwkjN0czW}

### Challenge 2: _"Learning Complex Usage"_
here we learn about programs that take arguments to their arguments, for example the find command which took the argument -name which took another argument which was the name of the file
here we had to run /challenge/challenge with an argument --printfile which prints the content of the file whose path was specified as an argument to this.
The file we have to print is /flag, so we could simply run the code /challenge/challenge --printfile /flag
pwn.college{sTpexrYQou95lwr_AXXMvQfrX6W.dVjM5QDLwkjN0czW}

### Challenge 3: _"Reading Manuals'_
In this challenge, there was a special way to access the flag, and this special way was mentioned in the manual of challege.
To access the manual of challenge, we would type man challenge where we could see in the description an argument called --sjripm NUM, which would display the flag when NUM was 742.

here, I first ran /challenge --sjripm 742, which did not give the flag, and then i ran /challenge/challenge --sjripm 742 which gave me the flag
pwn.college{s7I4jrY2LiZRpm1UoWbTgdL_1He.dRTM4QDLwkjN0czW}

### Challenge 4: _"Searching Manuals"_
This challenges teaches us how to navigate manuals, how to search using / and ? and navigate the results using n and N

here the challenge manual had a bunch of arguments and we had to find which one gave the flag as the output.
For this we type man challenge to open challenge manual and then i typed /flag to find some information related to flag
after scrolling through the results i found an argument --dsehw with a description which said this will give you the flag

on running /challenge/challenge --dsehw we get the flag  pwn.college{oQY_xywS8pQtW5aYvarJWfiOXsv.dVTM4QDLwkjN0czW}

### Challenge 5: _"Searching for manuals"_
In this challenge, running /challenge/challenge alone will not give us the flag, instead we need some argument which we need to search for using the man command.

first we type man man to check out all types of usage of man command, specifically how to search for a man page of another command. We can do this by using man -k [keyword]

Now obviously the keyword would be something related to our challege, such as "challenge", so after i typed man -k challenge, i got the output "qtgbhkbfun (1)       - print the flag!" 

now we need to use the man command to see what argument to run
upon doing man qtgbhkbfun we can see the argument --qtgbhk NUM where NUM is 771 would give us the flag.

So if we type /challenge/challenge --qtgbhk 771, we would get the flag.
pwn.college{Mq_OVHtVgI77bOhkb1Tf5uKng7f.dZTM4QDLwkjN0czW}


### Challenge 5: _"Helpful Programs"
here we learn to use the --help argument which gives us a details about a command, despite the command not having a man page.
first we run /challenge/challenge --help to see what do we have to run as argument to get the flag
here we get 2 interesting arguments: -g, which "gives the flag if given the correct value" and -p which gives the "correct value which runs -g"

so first we must run /challenge/challenge -p to get the value, which 912

then i ran /challenge/challenge -g, thinking it would ask me for the value later. However, i was presented with some error message
"usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: expected one argument"

after this i ran the value as an argument --> "/challenge/challenge -g 912" which gave me the flag pwn.college{sR9osOBuSjf_yFFn120IQ0g1gn2.ddjM4QDLwkjN0czW}

### Challenge 6: _"Help for builtins"_
here we learn about the help command.
typing "help" in itself would display the list of builtins and their syntax for how to use them.
first i ran help, thinking that challenge was replaced with some other command but instead that "challenge" took an argument "--secret" which took another argument "VALUE"

after this i ran help challenge which gave me the secret value :kdreD9l3

so i ran "challenge --secret kdreD9l3" and this gave me the flag.
pwn.college{kdreD9l3JzEZd3V0L0q02FhUj11.dRTM5QDLwkjN0czW}
