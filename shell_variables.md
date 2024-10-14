### Challenge 1: _"Printing variables"_
here the flag was put into a variable called FLAG
to print a variable need to to run `echo $_variable_name_`
so, to print the flag we will run " echo $FLAG" which will give us the flag
$ is used to _access_ variables
**flag: pwn.college{08gyhHhwmu8Hc2-Fn1eZVJj5EWd.ddTN1QDLwkjN0czW}**

### Challenge 2: _"Setting variables"_
Setting a variable is easy, we just run "_variable_name_=_value_" 
here, $ is not put before the variable because it can cause something called _variable expansion_ and there also must not be any spaces before and after the '='

To get the flag in this challenge, we needed to set a variable PWN with the value COLLEGE
on typing `"PWN=COLLEGE"` the flag was given to us 
**flag: pwn.college{cYmLEcNlzZqWfuibnbjRskCu-dI.dlTN1QDLwkjN0czW}**

### Challenge 3: _"Multi-word Variables"_
To store a value which contains more than one word, into a variable, we need to use double-quotes 
So in this challenge set the value of PWN to COLLEGE YEAH
for this, we will type `PWN="COLLEGE YEAH"`
this gives us the flag
**flag: pwn.college{ACMl0jm8sz-XnQYhjSmNVaiYXRX.dBjN1QDLwkjN0czW}**

### Challenge 4: "Exporting Variables"
so by default, variables are declared in the $ prompt, which is a child of the main process, sh.
if we set variable A=123, then type "sh" (to go to main process) and type echo $A, we will not get an output because A only exists in $
to change is this, we can type export A, which help us get value of A from any prompt
Here we needed to set PWN=COLLEGE and export that and set COLLEGE=PWN but not export that. After this we needed to run /challenge/run to get the flag
upon typing:
`export PWN=COLLEGE`
`COLLEGE=PWN`
`/challenge/run`

we got the flag
**flag: pwn.college{U2k_adR0V2q0iuZbpd6MSoCUFfA.dJjN1QDLwkjN0czW}**

### Challenge 5: _"Printing exported variables"_
Here we learn about the "env" command which prints every exported variable. There were a bunch of useless variables, and we had to find the FLAG variable
for this, i typed `env |grep FLAG`
this gave me the value of the flag
**flag: pwn.college{E6Tuc_AljZda3S4JcqmfY9yzYqx.dhTN1QDLwkjN0czW}**

### Challenge 6: _"Storing command output"_
To store the output of a command into a variable we can use $(_command_) 
Here we needed to store output of /challenge/run into PWN and then read it out
`PWN=$(/challenge/run)` will redirect the output of /challenge/run which is the flag into PWN
`echo $PWN` will read out the flag

**flag: pwn.college{gw1Ag8WYJcHfAzgXu1uBQacXu2y.dVzN0UDLwkjN0czW}**

### Challenge 7: _"Reading Input"_
Here we use the _read_ command.
If we type `read variable-name` and then input some value, the value will be stored in the variable
here we needed to store the value "COLLEGE" into PWN by using the read command
for that we would do
`read PWN`
`COLLEGE`
this would give us the flag 
**flag: pwn.college{cbYHrtG7H52tg24lPzmO15SC8Ls.dhzN1QDLwkjN0czW}**

### Challenge 8: _"Reading files"_
We can read a file by giving the file as standard input for `read` command by using '<'
Here we needed to read /challenge/read_me into pwn
so we would simply type
`read PWN < /challenge/read_me`
this would give the contents of read_me as input to `read` command and would read and store that input in PWN variable
