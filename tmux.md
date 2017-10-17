# Richard's tmux cheat sheet

* Metasyntactic variables are shown using `[brackets]`: these are placeholders to
be replaced with real values
* Default prefix key is _Ctrl+B_

## Command line

| Description       | Command line                                                   |
|-------------------|----------------------------------------------------------------|
| List sessions     | `tmux ls`                                                      |
| New session       | `tmux -s [session-name-or-index]`                              |
| Attach to session | `tmux attach-session -t [session-name-or-index]`               |
| Rename session    | `tmux rename-session -t [old-session-name] [new-session-name]` |
| Kill session      | `tmux kill-session -t [session-name-or-index]`                 |

## Controls

| Action | Shortcut  |
|--------|-----------|
| Detach | _[prefix key] d_ |
| List | _[prefix key] =_ |




==========================================          ==========================================
             TMUX COMMAND                                        WINDOW (TAB)
==========================================          ==========================================

List    tmux ls                                     List         ^b w
New          -s <session>                           Create       ^b c
Attach       att -t <session>                       Rename       ^b , <name>
Rename       rename-session -t <old> <new>          Last         ^b l               (lower-L)
Kill         kill-session -t <session>              Close        ^b &

==========================================          Goto #       ^b <0-9>
             CONTROLS                               Next         ^b n
==========================================          Previous     ^b p
                                                    Choose       ^b w <name>
Detach       ^b d
List         ^b =                                   ==========================================
Buffer       ^b <PgUpDn>                                         PANE (SPLIT WINDOW)
Command      ^b : <command>                         ==========================================

Copy         ^b [ ... <space> ... <enter>           Show #       ^b q
 Moving         vim/emacs key bindings              Split Horiz  ^b "                --------
 Start          <space>                             Split Vert   ^b %                   |
 Copy           <enter>                             Pane->Window ^b !
Paste        ^b ]                                   Kill         ^b x

==========================================          Reorganize   ^b <space>
             SESSION (Set of Windows)               Expand       ^b <alt><arrow>
==========================================          Resize       ^b ^<arrow>
                                                    Resize x n   ^b <n> <arrow>
New          ^b :new     ^b :new -s <name>
Rename       ^b $                                   Select       ^b <arrow>
List         ^b s                                   Previous     ^b {
Next         ^b (                                   Next         ^b }
Previous     ^b )                                   Switch       ^b o                  other
                                                    Swap         ^b ^o
                                                    Last         ^b ;



==========================================          ==========================================
             TMUX COMMAND                                        WINDOW (TAB)
==========================================          ==========================================

List    tmux ls                                     List         ^b w
New          -s <session>                           Create       ^b c
Attach       att -t <session>                       Rename       ^b , <name>
Rename       rename-session -t <old> <new>          Last         ^b l               (lower-L)
Kill         kill-session -t <session>              Close        ^b &

==========================================          Goto #       ^b <0-9>
             CONTROLS                               Next         ^b n
==========================================          Previous     ^b p
                                                    Choose       ^b w <name>
Detach       ^b d
List         ^b =                                   ==========================================
Buffer       ^b <PgUpDn>                                         PANE (SPLIT WINDOW)
Command      ^b : <command>                         ==========================================

Copy         ^b [ ... <space> ... <enter>           Show #       ^b q
 Moving         vim/emacs key bindings              Split Horiz  ^b "                --------
 Start          <space>                             Split Vert   ^b %                   |
 Copy           <enter>                             Pane->Window ^b !
Paste        ^b ]                                   Kill         ^b x

==========================================          Reorganize   ^b <space>
             SESSION (Set of Windows)               Expand       ^b <alt><arrow>
==========================================          Resize       ^b ^<arrow>
                                                    Resize x n   ^b <n> <arrow>
New          ^b :new     ^b :new -s <name>
Rename       ^b $                                   Select       ^b <arrow>
List         ^b s                                   Previous     ^b {
Next         ^b (                                   Next         ^b }
Previous     ^b )                                   Switch       ^b o                  other
                                                    Swap         ^b ^o
                                                    Last         ^b ;


## Build
