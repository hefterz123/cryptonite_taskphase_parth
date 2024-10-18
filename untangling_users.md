### Challenge 1: _"becoming root with su"_
the su comand is used to switch user to root. It asks for a password before switching to root, here the password was hack-the-planet.
after typing `su` it asks for password, and on typing password we get root access. Then we can simply `cat /flag` and get the flag
**flag: pwn.college{c3oTvBsA3RdiXVh5l6fK9YPBkde.dVTN0UDLwkjN0czW}**

### Challenge 2: _"other users  with  su"_
we can switch to a different user by giving the username as an argument to `su`. If we do not mention anything as argument, `su` directly runs as root.
Here we need to switch to "zardus" user, for this we will type `su zardus` then it will ask for the password, which is "dont-hack-me" and then we will `/challenge/run` to get the flag.
**flag: pwn.college{c3oTvBsA3RdiXVh5l6fK9YPBkde.dVTN0UDLwkjN0czW}**

### Challenge 3: _"cracking passwords"_
here, we got a leaked "/etc/shadow" in "/challenge/shadow-leak". 
If we do `cat /challenge/shadow-leak` we can see all users and their encrypted passwords. To decrypt these passwords we run `john /challenge/shadow-leak` this will give us the password for "zardus" user. 
After this we can do `su zardus` and log in with the password we got earlier. Then running `/challenge/run` will give us the flag
**flag: pwn.college{EwTCT8OXK7hzdr5AV3yenlKFM7e.ddTN0UDLwkjN0czW}**

### Challenge 4: _"using sudo"_
Here, if we ran `cat /flag`, it would say permission denied.
So instead we run `sudo cat /flag` which will run `cat /flag` as the root and give us the flag
**flag: pwn.college{Ib6lBRCsjMtBGDQIOzZXXx6OlrF.dhTN0UDLwkjN0czW}**
