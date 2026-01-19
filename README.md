# linux-permissions-security
## What is this project about
This project demonstrates how real breaches happens due to bad permissions and how to fix them.
## Experiment
- created different users (attacker and owner)
- created a secret file in one user (owner)
- tried to access the secret file using the other user (attacker)
- observed the security risks after changing permissions
- restored the security
## Key Findings
Using chmod 777 allows unauthorized users to read, write and execute files, which can lead to privilege abuse.
## Commands Used
- sudo adduser username
- cat > filename
- su - username
- cat /home/username/filename
- chmod 777 
