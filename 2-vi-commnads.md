# vi Editor Essentials Cheat Sheet

## 📂 Opening and Exiting

| Command       | Description                        |
| ------------- | ---------------------------------- |
| `vi filename` | Open or create a file in vi editor |
| `:w`          | Save the file                      |
| `:q`          | Quit (only if no changes made)     |
| `:wq` or `ZZ` | Save and quit                      |
| `:q!`         | Quit without saving                |
| `:x`          | Save and quit (same as :wq)        |

## 📝 Insert Mode (Entering Text)

| Command | Description                              |
| ------- | ---------------------------------------- |
| `i`     | Insert before the cursor                 |
| `I`     | Insert at the beginning of the line      |
| `a`     | Append after the cursor                  |
| `A`     | Append at the end of the line            |
| `o`     | Open a new line below                    |
| `O`     | Open a new line above                    |
| `Esc`   | Exit insert mode (return to normal mode) |

## 🔁 Navigation

| Command | Description                             |
| ------- | --------------------------------------- |
| `h`     | Move left                               |
| `l`     | Move right                              |
| `j`     | Move down                               |
| `k`     | Move up                                 |
| `0`     | Move to beginning of line               |
| `^`     | Move to first non-whitespace character  |
| `$`     | Move to end of line                     |
| `gg`    | Go to beginning of file                 |
| `G`     | Go to end of file                       |
| `:n`    | Go to line number `n`                   |
| `w`     | Jump forward to start of next word      |
| `b`     | Jump backward to start of previous word |

## ✂️ Editing (Normal Mode)

| Command    | Description                                     |
| ---------- | ----------------------------------------------- |
| `x`        | Delete character under cursor                   |
| `dd`       | Delete current line                             |
| `yy`       | Yank (copy) current line                        |
| `p`        | Paste after the cursor                          |
| `P`        | Paste before the cursor                         |
| `u`        | Undo last action                                |
| `Ctrl + r` | Redo last undone change                         |
| `r`        | Replace single character                        |
| `cw`       | Change word (delete word and enter insert mode) |

## 🔎 Search

| Command | Description                             |
| ------- | --------------------------------------- |
| `/text` | Search forward for "text"               |
| `?text` | Search backward for "text"              |
| `n`     | Repeat last search (same direction)     |
| `N`     | Repeat last search (opposite direction) |

## 🔧 Advanced

| Command         | Description                      |
| --------------- | -------------------------------- |
| `:set number`   | Show line numbers                |
| `:set nonumber` | Hide line numbers                |
| `:%s/old/new/g` | Replace all occurrences in file  |
| `:s/old/new/g`  | Replace all in current line      |
| `:!command`     | Run shell command (e.g., `:!ls`) |
