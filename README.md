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

* Initialize a repository
  
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

* **Reset**
  
  ```
  # Reset
  git reset <PREVIOUS_COMMIT_ID>  # or HEAD^
  ```

* **Revert**
  
  ```
  # Revert
  git revert <COMMIT_ID> ...  # rollback specific commits
  git revert <COMMIT_TO_ROLLBACK_TO>..<COMMIT_TO_ROLLBACK_FROM>  # range
  ```

* **Checkout**
  
  ```
  
  ```
  
  
