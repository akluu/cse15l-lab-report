# Week 2 Lab Report

## How to connect to your ieng6 account


1. **Installing VSCode**
    > This is not necessary, if you're on mac you can access your remote server through terminal.
    1. Go to [VSCode](https://code.visualstudio.com)
    2. Download
    <!-- end of the list -->
    It will look like:<br>
    ![image alt <](screenshots/Screen%20Shot%202022-04-08%20at%205.23.50%20PM.png)
2. **Remotely Connecting**
    1. Look up your account [here](https://sdacs.ucsd.edu/~icc/index.php), and reset your password.
    2. Your account is given we just need to add "@ieng6.ucsd.edu" to the end of the account.
    > i.e. my account is cs15lsp22aiv@ieng6.ucsd.edu
    3. To log in type the following into your terminal:
    > ssh *youraccount*@ieng6.ucsd.edu
    <!-- end of the list -->
    <br>
    It will look like:<br>

    ![image alt <](screenshots/Screen%20Shot%202022-04-08%20at%205.46.47%20PM.png)
    
    > You will most likely be prompted for a password, which is not shown here. In this case, just type the password you just resetted.
3. **Trying some commands**
    <br>
    [Here](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners) are some commands you can use in linux. Knowing the basics like pwd, ls, cd, etc. will be useful.<br>
    An example:<br>
    ![image alt <](screenshots/Screen%20Shot%202022-04-01%20at%204.43.25%20PM.png)
4. **Move Files with scp** <br>
    You can send files from computer to computer using the following command. <br>

    > scp **file* *youraccount*@ieng6.ucsd.edu:*directory*
    
    An example:<br>

    ![image alt <](screenshots/Screen%20Shot%202022-04-01%20at%204.43.10%20PM.png)
    > (Optional) scp works with multiple files so you can list multiple files and ":~/" can be  used for the default home directory.
5. **Setting an SSH Key**
    1. Log into your remote computer and make an ssh directory with the following command:
    > mkdir .ssh
    2. Go back to your personal computer and type the following command in the terminal:
    > ssh-keygen **(You do not need a passphrase)**
    3. Send your public key with the command:
    > scp /Users/*username*/.ssh/id_rsa.pub *youraccount*@ieng6.ucsd.edu:~/.ssh/authorized_keys
    4. Afterwards, as long as you're using the same computer, you can log into your remote computer without being prompted for a password.
    <br>

    If it works it should look like **(Notice how no password is required)**:
    ![image alt <](screenshots/Screen%20Shot%202022-04-01%20at%205.01.54%20PM.png)
6. **Optimizing Remote Running** <br>
    There are 2 things to know about optimizing remote running.
    1. You can run commands without logging into your remote computer with the command:
    > ssh *youraccount*@ieng6.ucsd.edu "*commands partitioned by ;*"
    2. The terminal will save your last ran command so you do not need to repeatedly type in long commands. You can just press the up arrow to call the last command.
    <br>
    Example:<br>
    
    ![image alt <](screenshots/Screen%20Shot%202022-04-01%20at%205.12.45%20PM.png)








    

