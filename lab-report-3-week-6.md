# Week 6 Lab Report

## **Streamlining ssh Configuration**
----
1.  Open up VScode and the integrated terminal.
2.  Type the following commands:
    >`cd ~/.ssh `

    >`pwd`
    
    It should output: /Users/*your_user*/.ssh
3.  Shift+Click or Command+Click the output to open up your .ssh directory in VScode.
4.  Make a file named "config" and fill it with the following options:

>Host _login_name_<br>
>&emsp;HostName _afterthe@_<br>
>&emsp;User _beforethe@_

### My personal configs:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%205.45.14%20PM.png)

### An example of ssh:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%207.11.50%20PM.png)
### An example of scp:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%207.13.35%20PM.png)

## **Setup Github Access from ieng6**
---
### Public ssh key on Github:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%207.19.09%20PM.png)
### Public and Private key on ieng6 server:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%207.20.21%20PM.png)
>Private key is id_rsa<br>
>Public key is id_rsa.pub

### Running git commands on remote server example:
![Image](screenshots/Screen%20Shot%202022-05-06%20at%207.30.40%20PM.png)
[Link to the commit above](https://github.com/akluu/cse15l-lab-report/commit/7b2a0fd37b799de41d6e8f00fb0ac0cdc5fb6c6d)

## **Copy whole directories with `scp -r`**
___
