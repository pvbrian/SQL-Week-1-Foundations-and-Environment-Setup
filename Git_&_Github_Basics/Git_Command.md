## Git Workflow Command Guide

- This workflow wants you to create a basic repo from your Github account, then clone it to vs code and then perform repository operations using git. (recall how we first created a basic repo from Github and added MIT Lisence)

1. Clone a Repository
- This means you download a copy of a remote repository to your local machine.
```shell
git clone <repository_url>
```
Example
```shell
git clone https://github.com/pvbrian/sql_fundamentals.git
```

2. Navigate to Project Directory
- This means you move into the project folder (the one you've cloned).
```shell
cd project_name
```
Example
```shell
cd sql_fundamentals
```

3. Create a New Branch
- Always work on a separate branch (not main or master).
- To create a new branch:
```shell
git checkout -b <branch_name>
```
Example:
```shell
git checkout -b dev_branch
```

4. Make Changes to Files
- Edit, add, or delete project files as needed.
- Example: Remember how we added new files example "create_database.sql"

5. Stage Changes
- Mark files you want to include in the next commit.
- PART A: To stage a specific file:
```shell
git add <file>
```
Example:
```shell
git add create_database.sql
```
- PART B: To stage ALL files:
```shell
git add .
```

6. Commit Changes
- This means you save staged changes with a descriptive message.
```shell
git commit -m "Your message here"
```
Example:
```shell
git commit -m "added create database sql file"
```

7. Push Branch to Remote
- This means you upload your branch and commits to the remote repository (The one on Github).
```shell
git push origin <branch_name>

or 

git push --set-upstream origin <branch_name>
```
Example:
```shell
git push --set-upstream origin dev_branch
```

8. Create a Pull Request (PR)
- On GitHub, open a PR to merge your branch into main.

9. Merge Branches (after PR approval)