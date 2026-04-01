# 1. `regex` (Regular Expressions)

Regular expressions, often shortened to regex, are a powerful tool for pattern-based selection. Understanding them is fundamental to mastering text manipulation in Linux. While there are many apps to learn Linux, diving into core concepts like `regular expression linux` is the quickest way to linux advanced proficiency. They use special notations, some of which are similar to wildcards like `*`.

Let's explore some of the most common regex operators, which are nearly universal across programming languages. We will use the following text as our example:

	`sally sells seashells`
	`by the seashore`

### Anchoring to the Start of a Line

The caret `^` symbol matches the beginning of a line. It ensures that your pattern appears only at the start.

`^by`

This pattern would match the line "by the seashore" but not "sally sells seashells"

### Anchoring to the End of a Line

The dollar `$` symbol matches the end of a line. It is the counterpart to the `^` anchor.

`seashore$`

This pattern would match the line "by the seashore" because it ends with "seashore".

### Matching any Single Character

The period `.` is a wildcard that matches any single character.

`b.`

In our example, this would match "by".

### Using Brackets for Character Sets

Brackets `[ ]` allow you to specify a set of characters to match. This provides more control than the `.` wildcard.

`s[ae]lls`

This would match "sells" and would also match "salls".

You can also use brackets to specify what *not* to match. When the caret `^` is the first character inside the brackets, it negates the set, matching any character *except* those listed.

`s[^e]lls`

This would match "salls" but not "sells".

Finally, brackets support ranges to define a large set of characters efficiently.

`d[a-c]g`

This pattern will match "dag", "dbg", and "dcg". Be aware that ranges are case-sensitive. For example, `[a-c]` will not match `A`, `B`, or `C`. 

# 2. Text Editors

Vim and Emacs are the main non-GUI text editors. They are essential tools for efficient manipulation of data and text files.

# 3. Vim (Vi Improved)

Vim is a powerful and highly configurable text editor built to enable efficient text editing. It is an improved version of the Vi editor, which is why it's called **Vim**, short for **Vi Improved**.

### What is Vim Vi Improved

As its name suggests, **vim vi improved** is a direct successor to the original Vi editor, which was a standard part of early Unix systems. Vim adds a vast number of features, including syntax highlighting, a comprehensive help system, multi-level undo, and extensive plugin support, making it a favorite among programmers and system administrators. The core philosophy of Vim is to allow for text manipulation without lifting your hands from the keyboard.

### Why Use Vim

One of the main advantages of Vim is its ubiquity. It is pre-installed on nearly every Linux distribution and is also available on macOS and Windows. This means you can rely on it being present on almost any server you connect to.

Furthermore, Vim is incredibly lightweight and fast. It starts instantly and can handle very large files without slowing down, a significant benefit when working on resource-constrained systems. Learning the basics of this **vim improved** editor is an essential skill for any Linux user.

### Getting Started with Vim

To start Vim, you can simply type the command in your terminal:

```bash
vim
```

This will open the editor with a blank buffer. To open a specific file, you can pass its name as an argument:

```bash
vim filename.txt
```

If the file exists, Vim will open it for editing. If it doesn't exist, Vim will open a new buffer and will create the file when you save it.

# 4. Vim Search Patterns

Searching for text is a fundamental task in any editor. Vim provides powerful and fast ways to perform a `vim search` directly from normal mode. Let's explore how to use these search patterns to improve your workflow.

### Forward Search

To perform a standard forward `vim search`, simply press the `/` key in normal mode, followed by your search term. When you press Enter, Vim will jump to the first occurrence of the term after your cursor.

```plaintext
My pretty file is very pretty.

/pretty

This will find the first "pretty" word after the cursor.
```

### Backward Search

Similarly, you can search backward from your cursor's position. Use the `?` key followed by your search term. Vim will find the first occurrence before your cursor.

```plaintext
My pretty file is very pretty.

?pretty

This will find the last "pretty" word in the file first.
```

### Navigating Search Results

Once a search is initiated, you can easily navigate through all the matches in the file.

- Press `n` to jump to the **next** match in the direction of the original search.
- Press `N` to jump to the **previous** match, moving in the opposite direction of the original search.

### Effective Vim Lookup

The `/` and `?` commands are the core of any `vim lookup` operation. Whether you need to find a specific function name, a variable, or just a word, this search mechanism is your primary tool. Mastering this simple `vim lookup` process is essential for efficient navigation and editing.

# 5. Vim Navigation

Now you may notice, the mouse is nowhere in use here. To navigate a text document in Vim, use the following keys:

- `h` or the left arrow - will move you left one character
- `j` or the down arrow - will move you down one line
- `k` or the up arrow - will move you up one line
- `l` or the right arrow - will move you right one character

# 6. Vim Inserting and Appending Text

In Vim, you'll primarily work in two modes: Normal mode for executing commands and Insert mode for typing text. To switch from Insert mode back to Normal mode, simply press the `Esc` key.

There are several commands to enter Insert mode, each placing the cursor at a different starting position for your text entry.

### Basic Insert Commands

The most fundamental way to start typing is with the `i` command.

- `i` – Insert text before the current cursor position.

This command switches you to Insert mode, allowing you to type directly into the file.

### Vim Append vs Insert

A common point of comparison is **vim append vs insert**. While both enter Insert mode, their starting points differ relative to the cursor. Understanding the **vim insert vs append** distinction is key to efficient movement and editing.

- `a` – **A**ppend text after the current cursor position.
- `I` – **I**nsert text at the beginning of the current line.
- `A` – **A**ppend text at the end of the current line.

Using `a` instead of `i` saves you a keystroke (moving the cursor one space to the right before inserting). Similarly, `A` is a powerful shortcut to immediately start typing at the end of a line. Mastering the `vim append` commands is a significant step in improving your editing speed.

### How to Vim Add Line

When you need to add new lines of text, you don't have to manually press Enter at the end of a line. Vim provides dedicated commands to open lines and immediately enter Insert mode.

- `o` – **o**pen a new line below the current line and enter Insert mode.
- `O` – **O**pen a new line above the current line and enter Insert mode.

These commands are extremely useful when you need to quickly **vim add line** while coding or writing.

Tip: You can prefix these commands with a number to repeat them. For example, typing `3o` in Normal mode will open three new blank lines below the current one and place you in Insert mode on the first of these new lines.

# 7. Vim Editing

Editing text in Vim is a powerful feature that relies on combining operators and motions from Normal mode. This approach allows you to efficiently delete, change, copy (yank), and paste (put) text. Before executing any commands, press `Esc` to ensure you are in Normal mode.

### Understanding Vim Operators and Motions

The core of Vim editing is the formula: `operator + motion`. An operator is an action (like `d` for delete), and a motion is a movement (like `w` for word). For example, `dw` combines the delete operator with the word motion to delete a word. You can also use counts to repeat an action, such as `2dw` to delete two words.

### Deleting Text in Vim

The delete operator is `d`. It's one of the most common Vim commands for text manipulation.

- `x` – Deletes the character directly under the cursor.
- `dw` – Deletes from the cursor to the beginning of the next word.
- `d$` – Deletes from the cursor to the end of the current line.
- `dd` – The `dd` command deletes the entire current line.
- `3dd` – Deletes three lines, starting from the current line.

### Changing Text

The change operator, `c`, works similarly to delete but places you into Insert mode after performing the action. This is useful for replacing text.

- `cw` – Changes the text from the cursor to the end of the word.
- `c$` – Changes text from the cursor to the end of the line.
- `cc` – Changes the entire current line.

### Copying and Pasting in Vim

In Vim, copying is called "yanking" (operator `y`), and pasting is called "putting."

- `yw` – Yanks (copies) a word.
- `yy` – Yanks the entire current line.
- `p` – Puts (pastes) the yanked text after the cursor or on the line below.
- `P` – Puts the text before the cursor or on the line above.

### Other Useful Editing Commands

This Vim guide wouldn't be complete without a few other handy commands.

- `r{char}` – Replaces the single character under the cursor with the specified character.
- `R` – Enters Replace mode, allowing you to overwrite text continuously until you press `Esc`.
- `J` – Joins the current line with the next one.
- `.` – Repeats the last change you made, a very powerful and efficient command.

Combining operators with different motions unlocks the full potential of this Linux text editor. For instance, `d}` deletes to the next paragraph, and `caw` changes "a word" (the word under the cursor including any surrounding space).

# 8. Vim Saving and Exiting

After you have finished editing a file, the next step is to save your changes and exit the editor. Vim provides several commands for this purpose, each with a specific function. All these commands are executed in Command-line mode, which you can enter by pressing `:`.

### How to Save in Vim Editor

To save the changes you've made to a file without exiting, you use the write command. This is the fundamental answer to the question "vim how to save".

- `:w` - Writes (saves) the current state of the file to disk.

### Exiting Vim

If you want to quit the editor, you have a couple of options depending on whether you want to save your changes.

- `:q` - Quits the editor. This command only works if you have no unsaved changes.
- `:q!` - Quits the editor and discards any unsaved changes. This is useful when you've made mistakes and want to revert to the last saved version of the file.

### Vim How to Save and Quit

Combining saving and quitting is a very common workflow. The `linux wq` command is a staple for many developers working on the command line.

- `:wq` - This command first writes (saves) the file and then quits. It's a two-in-one action for efficiency. Many users search for `vi write and quit`, and this command works for both Vi and Vim.
- `ZZ` - This is a shortcut equivalent to `:wq`. It saves the file if it has been modified and then quits. It's one character faster to type and a favorite among experienced Vim users.

### Undoing and Redoing Changes

While editing, you might need to reverse an action or bring it back. These commands are used in Normal mode (press `Esc` to enter).

- `u` - Undoes your last action.
- `Ctrl-r` - Redoes the last action that you undid.

Mastering these basic commands is the first step toward proficiency in Vim. As you become more comfortable, you'll find that these operations become second nature. For more advanced features, the official Vim documentation is an excellent resource.