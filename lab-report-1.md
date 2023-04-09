# Remote Access and FileSystem
This lab report details how to access your CSE15L-specific account and connect to the `ieng6` remote server.

## Accessing CSE15L Account
[https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)

First, click the link and enter your username (UCSD email w/o @ucsd.edu) and student ID. The CSE15L account username is listed under "Additional Accounts." 
If you have set a password (that you remember) for that account, you can ignore this next section.

There is a link that says `Global Password Change Tool`. Click on that and proceed to the password change tool.
![Image](https://emivcleave.github.io/cse15l-lab-reports/password-change.png)
Enter in your CSE15L account username and follow the password change instructions.

## VSCode
I didn't need to install VSCode as I already had it on my computer. However, this link is a tutorial for installation.

[VSCode Installation Tutorial](https://code.visualstudio.com/docs/setup/setup-overview)

Open VSCode once installed and open the terminal (mac: ctrl+`). 

## Remotely Connecting
Type in `ssh (cs15l username)@ieng6.ucsd.edu` to the terminal, replacing (cs15l username) with your actual username. 
It will prompt you to type in your password, but the letters will not show up when typing.
There may be an error message.
![Image](https://emivcleave.github.io/cse15l-lab-reports/error.png)
In this situation, I found that I was able to connect to the server by changing my wifi from UCSD-PROTECTED or RESNET-PROTECTED to my personal hotspot or eduroam, if they were avaiable.
When it connects, it should look something like this:


## Trying Commands
