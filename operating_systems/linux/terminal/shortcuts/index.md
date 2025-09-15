# Terminal shortcuts

## Jumping characters and words

- `Ctrl - f` to move the cursor forward one character at a time (same as the right arrow
)
- `Ctrl - b` to move the cursor backward one character at a time (same as the left arrow
)
- `Alt - f` to move the cursor forward one word;
- `Alt - b` to move the cursor backward one word;

## Swapping characters and words

- `Ctrl - t` to swap the current character under the cursor with the one preceding it;
- `Alt - t` to swap the current word under the cursor with the one preceding it;

## Killing lines, words and more

- `Ctrl - k` to kill the text from the current cursor location until the end of the
line;
- `Ctrl - u` to kill the text from the current cursor location to the beginning of the
line;
- `Alt - d` to kill the text from the current cursor location through the end of the
word;
- `Ctrl - w` to kill the text from the current cursor through beginning of the word;
- `Ctrl - d` to kill one character under the cursor;

## Reviving (Yanking) from the kill-ring

When we kill text using commands like `ctrl-k`, `ctrl-u`, etc., the "killed" text stored
in a memory in an area known as the "kill-ring".

- `Ctrl - y` - retrieve most recently killed text;
