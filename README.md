# Important Code for daily use

## Git Commands

* Check Git Configuration:
``` git config --list ```
* Add username:
``` git config --global user.name "your user name" ```
* Add user email:
``` git config --global user.email "yourname@email.com" ```
* Set a default branch to main:
``` git config --global init.defaultBranch main ```
* Add:
``` git add . ```
* Reset From Add .:
``` git reset ```
* Commit:
``` git commit -m "Messages" ```
* Push for the first time to the main branch:
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
* Forcefully push an existing branch like main
``` git push -f -u origin main ```
* Forcefully push like local development to remote main
``` git push --force origin origin/developmrnt:main ```
* Forcefully pull from remote main branch
``` git fetch origin && git reset --hard origin/main ```
* Check Status:
``` git status ```
* Check Status with time:
```
for f in $(git status --porcelain | awk '{print $2}'); do
  stat -c "%y %n" "$f"
done
```
* Check Origin 
``` git remote show origin ```
* Clone with default branch
``` git clone https://github.com/username/repository_name.git ```
* Clone with a specific branch
``` git clone -b branchname https://github.com/username/repository_name.git ```
* Switch to an existing branch
``` git checkout branchname ```
* Create and switch to a new branch from the current branch code
``` git checkout -b newbranchname ```
* Check branch
``` git branch ```
* Delete a branch (safe)
``` git branch -d branchname ```
* Delete a branch (force)
``` git branch -D branchname ```
* Delete a Remote Branch
``` git push origin --delete branchname ```
* Remove Untracked Data
``` git stash ```
* Branch Merging
``` git merge branchname ```
* Remove Directory from git
``` git rm -r directoryname ```
* Remove .env from git
``` git rm --cached --ignore-unmatch .env ```

*Find your password to pull your private repository*
* Log In to Your GitHub Account
* Go to Profile And Click Settings
* Click Developer settings
* Select Tokens (classic) under Personal access tokens
* Select Generate new token (classic) under Generate new token
* Check All And Click the Generate token Button.
* Copy The Token. That is your Password.
