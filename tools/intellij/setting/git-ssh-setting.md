# Intellij Git SSH Settings

Steps to integrate 'SSH' key in Intellij

1. Open 'PuTTYgen' application.
2. Click on 'File > Load private key'.
3. Choose your .ppk file from directory.
4. Click on 'Conversions > Export OpenSSH key'.
5. Save the file in 'C:\Users\(your username)\.ssh' folder with 'id_rsa' name.
6. Open Intellij.
7. Click on 'File > Settings'.
8. Expand 'Version Control'.
9. Expand 'Subversion'.
10. Click on 'SSH'.
11. Select 'Private key' radio button.
12. Select the generated file stored in 'C:\Users\(your username)\.ssh' folder.
13. Click on 'Ok' button.

Test configuration: Click 'VCS > Git > Fetch'. If 'Fetch Successful' message displays, your configuration is successful
