# Understand how real breaches happen due to bad permissions and how to fix them
#### 1. Create a user named owner:
  - sudo adduser owner
#### 2. Create a secret file in that account:
  - cat > secret.txt
#### 3. Create another user attacker:
  - sudo adduser attacker
#### 4. Switch to attacker user:      
  - su - attacker
#### 5. Try to access secret file from this user(attacker):
   - cat /home/owner/secret.txt
   - Output: permission denied.
   - Reason: the file is protected not only because of the file permissions but also by the directory permissions.
     * We should consider the permissions of the directory and also the permissions of the user too.
     * Since we know the issue why we were not able to access the file. we have to fix the  permissions.
#### 6. Fixing the permissions that are needed:
   - Directory:
     * sudo chmod 755 /home/owner
   - File:
      * su - owner      
      * chmod 777 secret.txt
#### 7. Now try again to access the file from the attacker:
  - su - attacker
  - cat > /home/owner/secret.txt
   * You can see the content of the file from attacker.
## The problems that might be faced due to this misconfiguring:
- It will give the access of read to the other accounts which may lead to misuse of the data of that account.
- Private files are no longer private.
## Restoring the security 
- Remove the read access of the owner to back.
   * sudo chmod 710 /home/owner
   * Changed to orginal permissions.
- Now try accessing the secret file again.
   * su - attacker
   * cat /home/owner/secret.txt
   * Output: permission denied
* Result : Regained the security.
## Mistakes that can be made 
- After the attack not changing it back to the orginal permissions.
- Not checking the permissions of the directory and files and trying to access the file.
- Trying to change the permissions as attacker instead of knowing that only root and the owner can modify the permissions.
