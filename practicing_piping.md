### Challenge 1: _"Redirecting output"_
we can redirect the output by using >
here we had to redirect output of "echo PWN" into a file called COLLEGE
upon doing echo PWN > COLLEGE we would get the flag

**flag: pwn.college{AYB43usaAGDp9ayzW2Uub12ATI0.dRjN1QDLwkjN0czW}**

### Challenge 2: _"Redirecting more output"_
Here, we redirect the ouput of /challenge/run into a file called myflag
On doing /challenge/run > myflag, it says that we have passed all tests and /flag file is now available (obviously in myflag file)
so we read the file by doing cat myflag and we get the flag.
**flag: pwn.college{sWSWmyQHd2GBnGp25XvhEmIrhCU.dVjN1QDLwkjN0czW}**

### Challenge 3: _"Appending output"_
If we redirect an output to a file, say, echo hi >file1. After this we type echo hello >file1
upon doing cat file1, it will read out, hello. This is because "hi" has been overwritten. So to ADD "hello" to file1 instead of replacing "hi" with "hello", we will need to use >> (echo hello >>file1)

here the flag is in 2 parts. First we needed to do /challenge/run > ~/the-flag to get the first part. After this we need to do /challenge/run >> ~/the-flag to get the second part. Now the entire flag is copied to ~/the-flag and we can read it by doing cat ~/the-flag

**flag: pwn.college{8789Lf8hFop2nLAJepigLVGHdd2.ddDM5QDLwkjN0czW}**


### Challenge 4: _"Redirecting errors"_
we can redirect the errors produced by mentioned the file descripton, in this case 2, before the >.
In this challenge we had to redirect the output of /challenge/run to myflag and the error to instructions
so for this we type: "/challenge/run >myflag 2>instructions"
upon doing cat instructions, we will get the instructions of the challenge
and doing cat myflag will give us the flag

**flag: pwn.college{MDAtVhUm7xTejt-sAhI9SxSNTpx.ddjN1QDLwkjN0czW}**

### Challenge 5: _"Redirecting input"_
To redirect input to programs, we use '<'
In this challenge, the first step was to put the value "COLLEGE" to a file "PWN". The second step was to redirect the input of "PWN" to /challenge/run

To do this, first we will do "echo COLLEGE >PWN".
Secondly, we'll do "/challenge/run < PWN"
and then this would give us the flag.

** flag: pwn.college{UC_QdNcYCT9S-LCx6rM9PnrhFmw.dBzN1QDLwkjN0czW}**

### Challenge 6: _"Grepping stored results"_
We learn to use the grep command here, which is used to search through files for a string.
First we needed to redirect output of /challenge/run to /tmp/data.txt and then search for the flag there

After typing /challenge/run > /tmp/data.txt, i typed grep flag which did not give me any output.
After this i typed grep flag /tmp/data.txt which listed every single word which included the word flag, however the flag i wanted was not here because it doesnt have the word "flag" in it.

So i typed grep pwn.college /tmp/data.txt and got the flag.

**flag: pwn.college{QP-uCugqwDd2orQS0NlV8278gla.dhTM4QDLwkjN0czW}**

### Challenge 7: _"Grepping live output"_
Here, we use grep to search within the output. We do this by using the pipe "|" in the same line as the command which gives the output.

So /challenge/run will give thousands of lines as output which would include the flag, so to search in the output without going through all those lines we will use | with grep

We will need to type /challenge/run | grep pwn.college, this will execute /challenge/run and then find for "pwn.college" in the output without executing all those lines.
Doing this will give us the flag

**flag: pwn.college{gIiBjFn-9gvfq0yGf9ePxMvKpUY.dlTM4QDLwkjN0czW}**

### Challenge 8: _"Grepping errors"_
Normally, the pipe only redirects output to the program, but to search for errors we must use ">&".
here we can specify the file descriptor, which we couldnt do in |. So to redirect both, the errors and output to another program we can do 2>&1

So to search through errors produced by /challenge/run to find the flag, we type:
/challenge/run 2>&1 | grep pwn.college
this will find and display the flag

**flag: pwn.college{kX5Rofco0y7gpaXnIQ0T_F568ju.dVDM5QDLwkjN0czW}**

### Challenge 9: _"Duplicating piped data with tee"_
Using tee shows us all the steps while copying the output into another file, this helps us in debugging.
We needed to copy the outputs of /challenge/pwn to /challenge/college.

So firstly, i tried "/challenge/pwn | tee /challenge/college" which showed some error message. So i ran cat /challenge/college to see the contents which has been copied, this showed a bunch of backend stuff which was not relevant to solving the challenge.
After this i tried running cat pwn, as it was mentioned that "pwn" wanted some special things to run. This showed i had to enter a special argument "--secret MuZcAG75" 

Then i ran /challenge/pwn --secret MuZcAG75 | /challenge/college which successfully copied the contents of /challenge/pwn to /challenge/college and gave me the flag.

**flag: pwn.college{MuZcAG75vFqYq_5jWA87jEybsZJ.dFjM5QDLwkjN0czW}**


### Challenge 10: _"Writing to multiple programs"_
here we need to copy output of /challenge/hack into input of /challenge/the and /challenge/planet
to copy as input, we need to use >()

first i tried running /challenge/hack | tee >(/challenge/the | /challenge/planet). This did not work
then i tried the same command without tee, which I knew would not work as i cannot split into two outputs without the tee command.

Then i tried writing the files seperately:
/challenge/hack | tee >(/challenge/the) >(/challenge/planet)
this gave me the flag

**flag: pwn.college{QNEErpzo5ZS1qt2lnzxixxApCBZ.dBDO0UDLwkjN0czW}**

### Challenge 11: _"Split-piping stderr and stdout"_
Here we had to redirect stderr of /challenge/hack to /challenge/the, and stdout of /challenge/hack to /challenge/planet

first i tried /challenge/hack | tee >(/challenge/planet) 2>(/challenge/the) which did not work
then i removed the tee, which again did not work. Then i removed the pipe.

Removing the pipe did not work, however it displayed a message explained the difference between cmd1 >(cmd2) and cmd 1> >(cmd2). The command i needed to use in this case was the latter

So i tried /challenge/hack > 2>(/challenge/the) > >(/challenge/planet). This gave me the flag

**flag: pwn.college{AYK6T-lnAsA0dFXih4C876e-k_w.dFDNwYDLwkjN0czW}**
