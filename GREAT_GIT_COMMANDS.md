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

⚙️ `git restore --source 3873c2f Readme.md`
- Restore the contents of specific file to match its state in specific commit

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

⚙️ `git notes add -m "Important performance improvement" a1b2`
- Add a note to the commit with hash a1b2

⚙️ `git notes show 65f7`
- Show the notes attached to the commit with hash 65f7

⚙️ `git notes list`
- List all notes in the repository

## Synchronization 
⚙️ `git reset --hard origin/main`
- Resets your local `main` branch to match the remote `origin/main` branch.

⚙️ `git cherry-pick c9614f7`
- Applies the specified commit (c9614f7) to the current branch.

## Branches, worktrees
⚙️ `git switch -c perf/optimize-directory-switching`
- Creates a new branch named `perf/optimize-directory-switching` and switches to it.

⚙️ git worktree add <path> <branch>
- Adds a new worktree at the specified path and checks out the specified branch. 

⚙️ git worktree list
- Lists all the worktrees associated with the repository.

⚙️ git worktree lock ../crusial_work
- Locks the specified worktree to prevent it from being pruned or deleted.

⚙️ git worktree unlock ../crusial_work
- Unlocks the specified worktree, allowing it to be pruned or deleted.

## Config settings
⚙️ `git config --list`
- Displays a list of all the configured Git settings.

⚙️ `git config --global pager.show-file batcat -l c --theme="ansi"`
- Show content of file with syntax highlight

⚙️ `git config --global alias.l "log --graph --format='format:%C(yellow)%h%C(reset) %s %C(magenta)%cr%C(reset)%C(auto)%d%C(reset)'"`
- Creates a global Git alias `l` for the command `git log --pretty=oneline --abbrev-commit`.
- Allows you to use `git l` instead of typing the full command every time.


## Bisect
⚙️ `git bisect start`
- Begin a bisect session to find a buggy commit
- Helps narrow down when a bug was introduced

⚙️ `git bisect bad 3tww`
- Mark the current or specified commit as "bad"
- Indicates the bug exists in this commit

⚙️ `git bisect good 28dq`
- Mark the current or specified commit as "good"
- Indicates the bug doesn't exist in this commit

⚙️ `git bisect reset`
- End the bisect session and return to the original HEAD
- Useful when you've found the buggy commit or want to abort

⚙️ `git bisect visualize`
- Show the remaining suspects in gitk
- Helps visualize the bisect process

⚙️ `git bisect log`
- Show the log of the bisect session
- Useful for reviewing your bisect steps

## Large projects
- Maintenance
  ⚙️ `git maintenance run --auto`

- Submodule
  https://android.googlesource.com/
  ⚙️ `git submodule add https://github.com/example/library.git`

* TechCorp/
  * backend/
    * api/
    * services/
    * database/
  * frontend/
    * web/
    * mobile/
  * docs/
    * api-docs/
    * user-guides/

  ⚙️ `git clone --no-checkout https://github.com/TechCorp/monorepo.git`
  ⚙️ `cd monorepo`
  ⚙️ `git sparse-checkout init --cone`
  ⚙️ `git sparse-checkout set frontend`
  ⚙️ `git checkout main`


- Partial clone
  ⚙️ `git clone --filter=blob:none  https://github.com/TechCorp/monorepo.git`



- Filter-branch
  ⚙️ `git filter-branch --tree-filter 'rm -f passwords.txt' HEAD`
  ⚙️ `git filter-branch --tree-filter 'rm -f sensitive_file.txt' HEAD`


- Rerere
  ⚙️ `git config --global rerere.enabled true`
