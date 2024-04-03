# tmux

## What is tmux

Tmux is a terminal multiplexor.

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

Create a new session with bame "test":

```shell
tmux new-session -s <session-name>
```

Deattach from session: `Ctrl+b`, `d`.

Attach to session:

```shell
tmux attach -t <session-name>
```

Session list:

```shell
tmux list-sessions
```

## Commands

Tmux commands start with `Ctrl+b` followed by the command. For example: `Ctrl+b`, `c` -
create a new window.

| Command | Meaning                 |
|---------|-------------------------|
| `c`     | Create a new window     |
| `2`     | Switch to window 2      |
| `%` | Split window vertically |
| left arrow, right arrow | If your window splitted vertically, you can switch between parts, using left/right arrows |
| `"` | Split window horizontally|
| up arrow, down arrow | If you window splitted horisontally, you can switch between parts using up/down arrows.|

## Settings

Tmux's settings stored in `~/.tmux.conf`

```
# use ctrl+q rather than ctrl+b for entering tmux commands
set-option -g prefix C-q

# change size of splited windows using mouse
set -g mouse on
```