# Basic Linux Commands and SSH/SCP Guide

## 1. Listing Files and Directories
```bash
ls
```

## 2. Creating a Directory
```bash
mkdir linux_practice
```

## 3. Navigating and Creating a File
```bash
cd linux_practice
touch test.txt
```

## 4. Displaying the Current Working Directory
```bash
pwd
```

## 5. Viewing Contents of /etc/passwd
```bash
cat /etc/passwd
```

# File and Directory Management

## 6. Creating Three Files
```bash
touch file1.txt file2.txt file3.txt
```

## 7. Moving file1.txt to a New Subdirectory
```bash
mkdir subdir
mv file1.txt subdir/
```

## 8. Renaming file2.txt
```bash
mv file2.txt renamed_file2.txt
```

## 9. Copying file3.txt to Parent Directory
```bash
cp file3.txt ../
```

## 10. Deleting a File and a Directory
```bash
rm renamed_file2.txt
rm -r subdir
```

# Setting Up SSH

## 11. Generating an SSH Key Pair
```bash
ssh-keygen -t rsa -b 2048
```
*Press ENTER to accept default location: `~/.ssh/id_rsa`*

## 12. Displaying the Public Key
```bash
cat C:\Users\user\.ssh\id_rsa.pub
```

## 13. Adding Public Key to a Service
- Copy the output and paste it in your remote server's SSH settings.

## 14. Give permission
chmod 600 ~/.ssh/authorized_keys
sudo systemctl restart ssh

# Logging into a Remote Server
ssh -i C:\Users\user\.ssh\id_rsa ubuntu@172.29.175.248



## 15. Creating a Directory on the Remote Server
```bash
mkdir remote_practice
```

# Transferring Files with SCP

## 16. Transferring example.txt to Remote Server
```bash
scp -i C:\Users\user\.ssh\id_rsa C:\Users\user\example.txt ubuntu@172.29.175.248:/home/ubuntu/remote_practice
```

## 17. Retrieving example.txt from Remote Server
```bash
scp -i C:\Users\user\.ssh\id_rsa ubuntu@172.29.175.248:/home/ubuntu/remote_practice/example.txt C:\Users\user\
then ls
```

---
This guide outlines basic Linux file operations, SSH setup, remote login, and SCP file transfer commands for beginners.

