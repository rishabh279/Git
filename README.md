## Git Commands

* **Setup**
  
  ```
  # Set credentials via terminal
  git config --global user.name <username>
  git config --global user.email <email>
  ```

* **Credentials Check**
  
  ```
  # Check credentials
  git config --global user.name
  git config --global user.email
  ```

* **Create**
  
  ```
  # Create project
  mkdir <project-name>
  cd <project-name>
  ```

* **Initialize a Repository**
  
  ```
  # Initialize git
  git init
  ```

* **Check files are untracked or yet to be committed**
  
  ```
  # Check status
  git status
  ```

* **Add to stage**
  
  ```
  git add .
  ```

* **Commit to repo**
  
  ```
  # Commit to local repo
  git commit -m "commit message"
  git branch -M main  # rename branch to main (if needed)
  ```

* **Push to remote**
  
  ```
  # Push to remote
  git remote add origin <git link to remote repo>
  git push -u origin main  # pushing the contents of our main branch to the remote repository
                           # origin is short for the name of the remote repository
  ```

* **Clone Repository**
  
  ```
  git clone <REMOTE_REPO_URL> <PATH_TO_PROJECT_DIR>
  ```

* **Clone Specific Branch**
  
  ```
  # Clone specific branch
  git clone -b <BRANCH> <REMOTE_REPO_URL> <PATH_TO_PROJECT_DIR>
  ```

* **Create a branch**
  
  ```
  # Create a new branch
  git checkout -b good
  ```

* **Switch between branches**
  
  ```
  # Switch between branches
  git checkout <BRANCH_NAME>
  ```

* **Create a Pull Request**
  
  ```
  gh pr create
  ```

* **Pull**
  
  ```
  git pull origin <branch name>
  ```

* **Delete Branches**
  
  ```
  # Delete branches
  git branch -d <BRANCH_NAME>  # local
  git push origin --delete <BRANCH_NAME>  # remote
  ```

* **Merge Branch**
  
  ```
  git merge <branch to be merged>
  git pull origin <changes to be merged from branch>
  ```

* **Rebase**
  
  ```
  git rebase <branch name>
  ```
  
  Reference Links:
  
  * https://www.youtube.com/watch?v=CRlGDDprdOQ
  
  * https://www.youtube.com/watch?v=OXtdxHTh2oY

* **Stash**
  
  ```
  git stash
  # Apply stash
  git stash list  # view all available stashes
  git stash apply 0  # apply a saved stash
  #If you have multiple stashes and you want to apply a specific one, you can do it like this (replace {n} with your stash number):
  git stash apply stash@{n}
  # Drop stash
  git stash drop 0  # remove the applied stash (optional)
  ```
  
* **Status**
  
  ```
  # Status
  git status
  git status -s  # short format
  ```

* **Log**
  
  ```
  # Log
  git log
  git log --oneline  # short version
  ```

* **Diff**
  
  ```
  # Diff
  git diff  # all changes between current working tree and previous commit
  git diff <COMMIT_A> <COMMIT_B>  # diff b/w two commits
  git diff <COMMIT_A>:<PATH_TO_FILE> <COMMIT_B>:<PATH_TO_FILE>  # file diff b/w two commits
  ```

* **Blame**
  
  ```
  # Blame
  git blame <PATH_TO_FILE>
  git blame -L 1,3 <PATH_TO_FILE>  # blame for lines 1 and 3
  ```

* **Restore**
  
  ```
  # Restore
  git restore -- <PATH_TO_FILE> <PATH_TO_FILE> # will undo any changes
  git restore --stage <PATH_TO_FILE>  # will remove from stage (won't undo changes)
  ```

* **Revert**
  
  ```
  # Revert
  git revert <COMMIT_ID> ...  # rollback specific commits
  git revert <COMMIT_TO_ROLLBACK_TO>..<COMMIT_TO_ROLLBACK_FROM>  # range
  # Let's say the hash of the commit is 'abc123'. You can revert it by running:
  git revert abc123
  #This will create a new commit that undoes the changes made in commit abc123. It's important to note that this doesn't 3 # delete any history. It simply applies the inverse of the given commit.
  ```

* **Soft Reset**

  ```
  # If you want to remove the commit from the history altogether, you can use the git reset command. To remove commit abc123 and all commits prior to it, but keep the changes in your working directory, you can do:
  git reset --soft abc123^
  ```

* **Reset**

  ```
  # Reset
  git reset <PREVIOUS_COMMIT_ID>  # or HEAD^
  # If you want to discard the changes as well, use:
  git reset --hard abc123^
  Note: Be careful with git reset --hard. It permanently discards changes, so you won't be able to recover them.
  ```

* **Unstage Changes**

  ```
  # To unstage changes in Git, you can simply use the git reset command.
  git reset
  # If you want to unstage a specific file you can use:If you want to unstage a specific file you can use:
  git reset <file>
  ```


* **Config for git pull**

  * `git config pull.rebase false`: This tells Git to create a new merge commit whenever you pull in changes.
  * `git config pull.rebase true`: This tells Git to rebase, which means to apply your changes on top of the changes you are pulling.
  * `git config pull.ff only`: This stands for "fast-forward only". It tells Git to only allow pulls that can be fast-forwarded.

  ```
  These are Git commands that configure how Git behaves when you perform a git pull. The git pull command is essentially the combination of git fetch followed by git merge or git rebase. The key difference between git merge and git rebase is how they integrate the commits from one branch into another.
  
  git config pull.rebase false: This is the default behavior of Git. When you execute git pull, Git will perform a git fetch to pull down all the new commits from the remote repository and then execute a git merge to merge those commits into your current branch. This process creates a new merge commit in your branch history.
  
  git config pull.rebase true : If you set this option, when you perform a git pull, Git will still do a git fetch to get the new commits, but instead of merging them, it uses git rebase. What this means is that Git will try to apply your changes as if you made them on top of the changes from the remote repository. There will be no merge commits and the commit history will be linear, as if you just checked out the latest version and then made your changes.
  
  To summarize, git config pull.rebase false will merge the commits (keeping trace of the fact that there were two separate branches that were later integrated), while git config pull.rebase true will rebase them (making it seem like all the work was done in a single, linear branch). The choice between them depends on whether you want to maintain a record of branch merges in your commit history.
  
  git config pull.ff only is a configuration setting for Git that alters how git pull behaves. The "ff" stands for "fast-forward."
  
  When you run git pull, Git fetches commits from the branch in the remote repository that corresponds to the branch you're currently on in your local repository. Then it needs to integrate those new commits into your current branch.
  
  When pull.ff is set to only, Git will only update (or "fast-forward") your branch if the new commits form a linear progression from the commits you have. This is traditionally the case if you haven't made any new commits on your branch since the last pull. Git can just move your branch pointer to point at the newest commit.
  
  If you have made new commits and pull.ff is set to only, Git will refuse to modify your branch, because doing so would require either a merge commit (if git pull behaved as git merge) or a rebase (if git pull behaved as git rebase).
  
  So, when you set git config pull.ff only, you're telling Git to only integrate new commits from git pull if the task can be performed as a straightforward, linear fast-forward. If a merge or rebase would be required, Git will give you a message to that effect and stop. You can then decide how you want to handle the situation.
  ```

* **To checkout a remote branch, you can follow these steps**

  ```
  1. First fetch all the remote branches using:
  git fetch origin
  
  2. Now we can checkout to the remote branch using:
  git checkout -b review-lbc origin/review-lbc
  ```

* ##### Fork a repository


    * https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo



* ##### Syncing a fork


    * https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork



* ##### Choosing license for opensource repository


  * https://choosealicense.com/

* Fork a repository

* Fork a repository

* Fork a repository

* Fork a repository

* Fork a repository
