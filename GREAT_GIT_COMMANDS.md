# Great Git Commands

⚙️ `git log --pretty=oneline --abbrev-commit`
* Displays the commit history in a concise, one-line format with abbreviated commit hashes.
* Useful for quickly scanning through commit messages.

⚙️ `git config --global alias.l "log --pretty=oneline --abbrev-commit"`
- Creates a global Git alias `l` for the command `git log --pretty=oneline --abbrev-commit`.
- Allows you to use `git l` instead of typing the full command every time.

⚙️ `git show --pretty=fuller a6bdb68`
- Displays detailed information about the specified commit (a6bdb68 in this case).
- The `--pretty=fuller` option provides a more comprehensive view of the commit, including the commit message, author, date, and file changes.

⚙️ `git rebase -i --root`
- Starts an interactive rebase from the root commit of the current branch.
- Allows you to rewrite commit history by squashing, reordering, or modifying individual commits.
- Useful for cleaning up the commit history before merging or pushing changes.

⚙️ `git cherry-pick c9614f7`
- Applies the changes introduced by the specified commit (c9614f7) to the current branch.
- Helpful when you need to apply a specific commit from another branch without merging the entire branch.

⚙️ `git switch -`
- Switches to the previously checked-out branch.
- Convenient for quickly switching between branches when working on multiple tasks.

⚙️ `git config --list`
- Displays a list of all the configured Git settings.
- Useful for inspecting and verifying Git configurations.

⚙️ `git fetch origin`
- Fetches the latest changes from the remote repository (origin) without merging them into your local branch.
- Allows you to review the changes before merging or integrating them.

⚙️ `git reset --hard _origin/main_`
- Resets your local `main` branch to match the remote `origin/main` branch.
- Discards all local changes and updates your local branch to match the remote.
- Use with caution, as this operation cannot be undone.

⚙️ `git diff main origin/main`
- Shows the differences between your local `main` branch and the remote `origin/main` branch.
- Helps you identify the changes that need to be merged or resolved before pushing your local changes.

⚙️  `git push --force origin main`
- Forcefully pushes your local `main` branch to the remote `origin` repository, overwriting the remote branch.
- Use with caution, as it can overwrite commits on the remote branch.

⚙️ `git config --global alias.a '!f() { git add . && git commit -m "$1" && git push origin main; }; f'`
- Creates a global Git alias `a` that allows you to stage all changes, commit with a provided message, and push to the remote `main` branch with a single command.
- Example usage: `git a "My commit message"`.

⚙️ `git reset @~`
- Resets the current branch to the previous commit (one commit behind the current HEAD).
- Useful for undoing the last commit without losing the changes.

⚙️ `git switch -c perf/optimize-directory-switching`
- Creates a new branch named `perf/optimize-directory-switching` and switches to it.
- Convenient for starting work on a new feature or bug fix.

⚙️ `git difftool -t meld`
- Opens the Meld visual diff tool instead of standard git diff pager.
