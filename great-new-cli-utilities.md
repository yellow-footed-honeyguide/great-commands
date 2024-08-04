# GREAT New CLI Utilities

## batcat
- `batcat`: A powerful syntax highlighting tool for the terminal.
- `batcat --list-themes`: Lists all available syntax highlighting themes.
- `batcat --theme="Coldark-Cold" file.txt`: Displays the content of `file.txt` with the "Coldark-Cold" theme.

## btop (bashtop, bpytop)
- `btop`: An interactive process viewer with a user-friendly interface.

## viddy
- `viddy "echo 'Private + Shared = RAM used Program'; sudo ps_mem | tac | head -n -1"`: Displays the RAM usage of processes with a helpful explanation.

## duf
- `duf`: A disk usage utility that visualizes disk usage in a user-friendly way.

## ncdu
- `ncdu`: A disk usage utility that visualizes disk usage in interactive mode.

## dust
- `dust`: A simple and user-friendly disk usage analyzer.

## iotop
- `iotop`: Monitors disk I/O usage in real-time.
- `iotop --only`: Displays only the processes that are actively performing I/O operations.
- `iotop --only --processes`: Displays only the processes that are actively performing I/O operations and their process IDs.

## nethogs
- `sudo nethogs`: Monitors network traffic by process.

## scc (Source Code Counter)
- `scc`: Counts the lines of code in various programming languages.
- `scc --exclude-lang="PO File"`: Excludes PO files from the line count.
- `scc --by-file`: Displays the line count for each file.
- `scc --by-file --format html`: Generates an HTML report with the line count for each file.
- `sysvinit > my_page.html`: Generates an HTML report for the `sysvinit` project.
- `scc --format html linux-6.8.4 > my_page.html`: Generates an HTML report for the `linux-6.8.4` project.

## ripgrep (rg)
- `rg`: A fast and powerful line-based text search tool.
- `rg -w "my_word"`: Searches for whole-word occurrences of "my_word".
- `rg -w -i "my_word"`: Searches for whole-word occurrences of "my_word" (case-insensitive).


## diff-so-fancy
- `diff-so-fancy`: A user-friendly and colorful alternative to the traditional `diff` command.
- `diff file1.txt file2.txt`: Displays the differences between `file1.txt` and `file2.txt` with syntax highlighting.
- `diff --color -u file1.txt file2.txt`: Displays the unified diff between `file1.txt` and `file2.txt` with color highlighting.
- `diff -u file1.txt file2.txt | diff-so-fancy`: Pipes the unified diff output to `diff-so-fancy` for better formatting.

