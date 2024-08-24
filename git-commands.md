# Git Commands Cheat Sheet

Here are the most frequently used Git commands you must know as a DevOps Engineer.

**1. git help**

Use git help command to get help from git about any command.

**2. git version**

The git version command displays the version of Git installed on our system. 

**3. git init**

The command git init is used to initialize a new Git repository in the current directory.

**4. git clone <repository_url>**

You'll get the full copy of the remote git repository on your VM.

**5. git status**

The git status command displays the state of the working directory and the staging area.

**6. git add**

This command adds a specific file to the staging area in Git.

**7. git commit -m "message"**

This command is used to create a new commit in your Git repository.

**8. git log**

Display the entire commit history using the default format.

**9. git diff**

The git diff command helps you see, compare, and understand changes in your project.

**10. git config user.name <your name here>**

Define author name to be used for all commits in current repo

**11. git config --global user.name yournamehere**

Define the author name to be used for all commits, change your name accordingly.

**12. git config --global user.email abc@gmail.com**

Define the author email to be used for all commits, change your email accordingly.

**13. git log -<put the log limit>**

For instance, git log -3 will print the first 3 commits.

**14. git log --oneline**

Condense each commit to a single line

**15. git log -p**

Display the full diff of each commit.

**16. git log --stats**

Share the details about the files which were altered and the relative number of lines that were added or deleted from each of them.

**17. git log --author=author_name**

Filter the commit history and search by the author name.

**18. git log --grep=commit message**

Search for commits with a commit message.

**19. git log --graph --decorate**

This command draws a text based graph of commits on the left side.

**20. git commit --amend**

Change the last commit message.

**21. git branch -a**

Lists all the branches.

**22. git checkout branch_name**

Switch between the different branches.

**23. git branch yourbranchname**

Create a new branch, replace the branch name.

**24. git checkout -b yournewbranchname**

Create a new branch and point the HEAD to that branch.Replace the branch name.

**25. git merge my_branch**

Merge the my_branch into the current branch.

**26. git revert commit_id**

Revert the commit

**27. git remote -v**

Get the remote repo URL.

**28.** **git remote add origin repo_URL**

Create a new connection to a remote repo.

**29.** **git pull origin master**

Pull the specified remote’s copy of current branch and immediately merge it into the local copy.

**30. git fetch origin master**

It will just fetch the changes but it will not download those changes on your local repo.

**31.** **git push**

Push the branch to <remote>, along with necessary commits and objects.

**32.** **git push --force**

Forcefully push the changes.

**33.** **git push --all**

Push all of your local branches to the specified remote

**34. git stash**

Git stash temporarily shelves or stashes changes made to your working copy so you can work on something else, and come back and re-apply them later on.

**35. git rebase**

Rebase the current branch onto another branch.

**36. git diff**

Show difference between working directory and last commit.

**37. git diff --cached**

Show difference between staged changes and last commit

**38. git reset**

Show difference between staged changes and last commit.

**39. git reset --hard**

Reset staging area and working directory to match most recent commit and overwrites all changes in the working director

**40. git reset commit**

Move the current branch tip backward to <commit>.

**41. gh** 

Work with GitHub CLI, we need to install it first with "apt install gh"

**42. gh auth login**

Login with token into your GitHub account from Linux VM.

**43. gh auth logout**

Logout from GitHub account on your VM.

**44. gh repo create**

To create a new repository from scratch.

**45. gh repo delete**

To remove the GitHub repo using the GitHub CLI

**46. gh repo rename**

To rename your repository.

**47. gh repo view**

To view the repository on the Linux terminal.

**48. gh actions**

GitHub CLI command for GitHub Actions CICD workflows.

**49. gh run list**

List down GitHub Actions recent workflow runs.

**50. gh run view**

Run this command to view any workflow run.

Don't worry, we'll be going to learn CICD and GitHub Actions in the next lectures, so make sure to subscribe ;)
