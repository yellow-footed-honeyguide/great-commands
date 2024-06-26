# Great Git Commands

## Undoing things
⚙️ `git switch -`
- Switches to the previously checked-out branch.

⚙️ `git rebase -i --root`
- Starts an interactive rebase from the very first commit of the current branch.

⚙️ `git reset @~`
- Resets the current branch to the previous commit (one commit behind the current HEAD).

⚙️ `git reset @~3`
- Resets the current branch to the 3 commit ago.

⚙️ `git restore .`
- Revert all file modifications and restore the branch to its state at creation

⚙️ `git commit -a --amend --no-edit`
- Add changes to files in the latest commit
- Useful when you forget edit something before commit

## Show 
⚙️ `git log --pretty=oneline --abbrev-commit`
* Displays the commit history in a concise, one-line format with abbreviated commit hashes.

⚙️ `git show --pretty=fuller a6bdb68`
- Displays detailed information about the specified commit (a6bdb68 in this case).
- The `--pretty=fuller` option provides a more comprehensive view of the commit, including the commit message, author, date, and file changes.

⚙️ `git difftool -t meld`
- Opens the Meld visual diff tool instead of standard git diff pager.

⚙️ `git diff main origin/main`
- Shows the differences between your local `main` branch and the remote `origin/main` branch.

⚙️ `git show feature-branch:example.txt`
- Show content of file from another branch

⚙️ `git restore --source 3873c2f Readme.md`
- Restore the contents of specific file to match its state in specific commit

## Synchronization 
⚙️ `git reset --hard origin/main`
- Resets your local `main` branch to match the remote `origin/main` branch.

⚙️ `git cherry-pick c9614f7`
- Applies the specified commit (c9614f7) to the current branch.

## Branches, worktrees
⚙️ `git switch -c perf/optimize-directory-switching`
- Creates a new branch named `perf/optimize-directory-switching` and switches to it.

## Config settings
⚙️ `git config --list`
- Displays a list of all the configured Git settings.

⚙️ `git config --global pager.show-file batcat -l c --theme="ansi"`
- Show content of file with syntax highlight

⚙️ `git config --global alias.l "log --graph --format='format:%C(yellow)%h%C(reset) %s %C(magenta)%cr%C(reset)%C(auto)%d%C(reset)'"`
- Creates a global Git alias `l` for the command `git log --pretty=oneline --abbrev-commit`.
- Allows you to use `git l` instead of typing the full command every time.

⚙️ `git config --global alias.a '!f() { git add . && git commit -m "$1" && git push origin main; }; f'`
- Creates a global Git alias `a` that allows you to stage all changes, commit with a provided message, and push to the remote `main` branch with a single command.
- Example usage: `git a "My commit message"`.

⚙️ `git config --global alias.rdiff '!f() { git fetch && git diff --color=always --exit-code origin/$(git branch --show-current) | diff-so-fancy | less --tabs=4 -RFX; }; f'`
- Show diff in user-friendly style between remote and local
