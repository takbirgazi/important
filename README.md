# Important Code for daily use

## Git Commands

* Check Git Configuration:
``` git config --list ```
* Add user name:
``` git config --global user.name "your user name" ```
* Add user email:
``` git config --global user.email "yourname@email.com" ```
* Set a default branch to main:
``` git config --global init.defaultBranch main ```
* Add:
``` git add . ```
* Commit:
``` git commit -m "Messages" ```
* Push First Time To Main Branch:
   ``` git push -u origin main ```
   Next Time:
   ``` git push ```
* Remove The Last Commit
``` git reset --soft HEAD~1 ```
* Pull Existing Project
``` git pull ```
* Pull from Other Branch
``` git pull origin branchname ```
* Check Remote Repository
``` git remote -v ```
* Add Remote Repository
```git remote add origin https://github.com/username/repository_name.git```
* Change Remote Repository
``` git remote set-url origin https://github.com/username/new_repository_name.git ```
* Remove Remote Repository
```git remote remove origin```
* Push Forcefully Existing Branch like main
``` git push -f -u origin main ```
* Check Origin 
``` git remote show origin ```
* Clone with default branch
``` git clone https://github.com/username/repository_name.git ```
* Clone with specific branch
``` git clone -b branchname https://github.com/username/repository_name.git ```
* Switch an existing branch
``` git checkout branchname ```
* Create and Switch a new branch with the current branch code
``` git checkout -b newbranchname ```
* Check branch
``` git branch ```
* Delete a branch
``` git branch -d branchname ```
* Branch Merging
``` git merge branchname ```
* Remove .env from git
``` git rm --cached --ignore-unmatch .env ```

*Find your password to pull your private repository*
* Log In to Your GitHub Account
* Go to Profile And Click Settings
* Click Developer settings
* Select Tokens (classic) at Personal access tokens
* Select Generate new token (classic) at Generate new token
* Check All And Click the Generate token Button.
* Copy The Token. That is your Password.
