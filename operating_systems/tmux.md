# tmux

## What is tmux

Tmux is a terminal multiplexor.

One of the more popular benefits of tmux is that it keeps your session running even you
are no longer connected to the server.

## Installation

Install tmux (Ubuntu):

```shell
sudo apt install tmux
```

## Sessions

Create a new session

```shell
tmux
```

Create a new session with name "test":

```shell
tmux new-session -s <session-name>
```

Deattach from session: `Ctrl+b`, `d`.

Attach to session:

```shell
tmux attach -t <session-name>
# or
tmux a -t <session-name>
```

Session list:

```shell
tmux list-sessions
# or
tmux ls
```

## Commands

Tmux commands start with `Ctrl+b` followed by the command. For example: `Ctrl+b`, `c` -
create a new window.

| Command | Meaning                 |
|---------|-------------------------|
| `c`     | Create a new window     |
 | `d`    | Deattach from session   |
| `2`     | Switch to window 2      |
| up arrow, down arrow |  |

### Panes

tmux gives us the ability to create horizontal and vertical splits.

Create a __vertical__ split: `Ctrl+b` -> `%`

If your window split vertically, you can switch between panes, using
__left/right arrows__

Create a __horizontal__ split: `Ctrl+b` -> `"`

If you window split horizontally, you can switch between parts using __up/down arrows__.

If we want to close some pane we can type `exit` or `Ctrl+b` -> `x` and press `y` to
confirm.

## Settings

Tmux's settings stored in `~/.tmux.conf`

```
# use ctrl+q rather than ctrl+b for entering tmux commands
set-option -g prefix C-q

# change size of splited windows using mouse
set -g mouse on
```