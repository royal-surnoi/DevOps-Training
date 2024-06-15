The `vi` editor is a powerful text editor available in almost all Unix-like operating systems. Here is a list of essential commands for the `vi` editor:

### Basic Mode Switching
- **`i`**: Switch to insert mode to start inserting text before the cursor.
- **`I`**: Switch to insert mode to start inserting text at the beginning of the line.
- **`a`**: Switch to insert mode to start appending text after the cursor.
- **`A`**: Switch to insert mode to start appending text at the end of the line.
- **`o`**: Open a new line below the current line and switch to insert mode.
- **`O`**: Open a new line above the current line and switch to insert mode.
- **`Esc`**: Return to normal mode from insert mode.

### Basic Navigation
- **`h`**: Move the cursor left.
- **`j`**: Move the cursor down.
- **`k`**: Move the cursor up.
- **`l`**: Move the cursor right.
- **`w`**: Move the cursor to the beginning of the next word.
- **`b`**: Move the cursor to the beginning of the previous word.
- **`0`**: Move the cursor to the beginning of the line.
- **`$`**: Move the cursor to the end of the line.
- **`G`**: Move the cursor to the end of the file.
- **`gg`**: Move the cursor to the beginning of the file.
- **`Ctrl + f`**: Move one screen forward.
- **`Ctrl + b`**: Move one screen backward.

### Editing Text
- **`x`**: Delete the character under the cursor.
- **`dd`**: Delete the current line.
- **`dw`**: Delete from the cursor to the end of the word.
- **`d$`**: Delete from the cursor to the end of the line.
- **`u`**: Undo the last change.
- **`Ctrl + r`**: Redo the last undone change.
- **`yy`**: Yank (copy) the current line.
- **`yw`**: Yank (copy) the current word.
- **`p`**: Paste the yanked text after the cursor.
- **`P`**: Paste the yanked text before the cursor.
- **`r`**: Replace the character under the cursor.
- **`R`**: Switch to replace mode to overwrite text.

### Searching and Replacing
- **`/pattern`**: Search forward for `pattern`.
- **`?pattern`**: Search backward for `pattern`.
- **`n`**: Repeat the last search in the same direction.
- **`N`**: Repeat the last search in the opposite direction.
- **`:%s/old/new/g`**: Replace all occurrences of `old` with `new` in the entire file.
- **`:s/old/new/g`**: Replace all occurrences of `old` with `new` in the current line.

### Saving and Exiting
- **`:w`**: Save the file.
- **`:q`**: Quit `vi`.
- **`:wq`**: Save the file and quit `vi`.
- **`:x`**: Save the file and quit (similar to `:wq`).
- **`:q!`**: Quit `vi without saving changes.

### Visual Mode
- **`v`**: Start visual mode to select text character by character.
- **`V`**: Start visual line mode to select whole lines.
- **`Ctrl + v`**: Start visual block mode to select a rectangular block of text.
- **`y`**: Yank (copy) the selected text.
- **`d`**: Delete the selected text.
- **`>`**: Indent the selected text.
- **`<`**: Unindent the selected text.

These commands cover the basics of using `vi` for editing files. There are many more advanced commands and options available, but these should be sufficient to get started.