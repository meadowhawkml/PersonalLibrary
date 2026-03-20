
# 1. The Shell

## What is the Linux Shell

The first step to understanding Linux is understanding the **Linux Shell**. The Shell is a powerful program that accepts your typed commands and passes them to the operating system to execute. If you've used a graphical user interface (GUI), you might have encountered applications like "Terminal" or "Console". These are simply programs that open a shell session for you. Throughout this course, we will explore the capabilities of the shell and the many **Linux Commands** available.

### Understanding Bash

- Bash (Bourne Again Shell) is the default shell for most Linux distros.
	- While other shells like ksh, zsh, and tsch exist, mastering Bash provides a solid foundation for working with any Linux system

## The Shell Prompt

- When you open a terminal, you'll be greeted by the shell prompt. Its appearance can vary between distributions, but it typically follows this format:
	- `username@hostname:current_directory$`
- The *$* symbol at the end indicates that the shell is ready to accept commands from a regular user. You do not type this symbol when entering commands; it is purely informational.

#### Your First Linux Command

- Let's start with one of the most **basic Linux commands for beginners:** *echo*. This command is straightforward - it simply displays, or "echoes", the text you provide as arguments back to the terminal
- e.g. `echo` Hello World

# 2. `pwd` (Print Working Directory)

In Linux, a core concept is that everything is treated as a file. These files are organized within a hierarchical structure known as the filesystem. Understanding this structure is key to navigating your system effectively.

## The Directory Tree in Linux

- The entire filesystem starts from a single top-level directory called the root directory, represented by a forward slash ( */* ).
- From the root, the **directory tree in Linux** branches out into various subdirectories, which can contain files and further subdirectories.
- A simplified example of the structure

/ 
|-- bin 
| |-- file1 
| |-- file2 
|-- etc 
| |-- file3 
| `-- directory1 
| |-- file4 
| `-- file5 
|-- home 
|-- var

## Understanding File Paths

The location of any file or directory is described by its path. A path is a sequence of directories that leads from a starting point to a specific destination. For example, if you have a folder named *pete* inside the */home* directory, and a *Movies* folder inside *pete*, the full path would be */home/pete/Movies*.

# 3. `cd` (Change Directory)

To move around the Linux filesystem, you'll use paths to specify your destination. The primary tool for this is the *cd* (change directory) command. Understanding how to use this *cd linux command* is a fundamental skill for working in the terminal or *cd command prompt*. 

## Understanding Paths

There are two ways to specify a path: **Absolute** and **Relative**.

- **Absolute Path**: This is the full path starting from the root directory ( */* ). The root is the top-level directory in the filesystem. Any path that begins with */* is an absolute path. For example: */home/pete/Desktop*.
- **Relative Path**: This path is relative to your current location in the filesystem. If you are in */home/pete/Documents* and want to access a subdirectory named *taxes*, you don't need the full path. You can simply use the relative path: *taxes/*.

## Using the cd Command

- Once you understand paths, you can use the *cd command* to change your current directory.
- To change to a specified directory, for example *Pictures*, using an absolute path you would time:
	- *cd /home/pete/Pictures*
- This command moves you directly to the *Pictures* directory.

## Navigating to a cd Folder

- If you are already in a directory and want to move to a sub-directory, you can use a relative path.
- For example, if your current location is */home/pete/Pictures* and it contains a *cd folder* named *Hawaii*, you can navigate to it with:
	- *cd Hawaii*

### Essential Navigation Shortcuts

Navigating with full paths can be tedious. Fortunately, the shell provides several shortcuts to make moving around much faster.

-  `.` (current directory): Represents the directory you are currently in.
- `..` (parent directory): Moves you one level up to the directory containing your current one.
- `~` (home directory): A shortcut to your personal home directory, like `/home/pete`.
- `-` (previous directory): Takes you back to the last directory you were in.

# 4. `ls` (List Directories)

## Basic Usage of the ls Command

By default, the `ls` command will list the directories and files in your current directory. However, you can also specify a path to list the contents of a different directory. Ex:

`ls`
`ls /home/pete`

### Viewing Hidden Files

Note that *not all files in a directory are visible by default*. In Linux, *filenames that start with a dot (`.`) are hidden.* You can view them by using the `cmd ls` with the `-a` flag, which stands for "all"

`ls -a`

### Getting Detailed Information

Another essential `ls` flag is `-l` for "long". This option provides a detailed list of files in  a long format. This will show you detailed information, starting from the left:
- File permissions
- number of links
- owner name
- owner group
- file size
- timestamp of last modification
- file or directory name

### Sorting in Reverse Order

Sometimes you may want to change the sort order. The `ls -r command` lists files and directories in reverse alphabetical order. The `linux ls -r` option is particularly handy when you want to see the last items in a long list first.

`ls -r`

### Combining Command Flags

Commands have flags (also called arguments or options) to add more functionality. As we saw with `-a` and `-l`, you can combine them into a single command like `ls -la`. The order of the flags *usually* doesn't matter, so `ls -al` would work identically. You can also add the reverse flag: `ls -lar`.

`ls -la`

# 5. `touch`

The `touch` command is a standard utility on Unix-like operating systems. While its primary purpose is to change file timestamps, it is also commonly used to create new, empty files.
## Creating New Files

The simplest way to create an empty file is by using the `touch` command followed by a filename. If the file does not exist, `touch` will create it for you. This is a fundamental `bash touch` operation for scripting and daily tasks.

`touch nameofnewfile`

After running this command, a new empty file named `nameofnewfile` will appear in your current directory. You can create multiple files at once by listing their names.

`touch file1.txt file2.txt file3.log`

### Updating File Timestamps

The original function of the `touch command in linux` is to update the access and modification timestamps of a file or directory. If you use `touch` on an existing file, it will update its timestamps to the current time.

You can verify this by using `ls -l` to check a file's timestamp, running `touch` on it, and then checking again.

*\# Check the original timestamp*
`ls -l nameofnewfile`

*\# Update the timestamp*
`touch nameofnewfile`

*\# Check the new timestamp*
`ls -l nameofnewfile`

> [!info] **Advanced Timestamp Control**
> The `linux touch` command also provides options for more precise timestamp manipulation

### Using a Reference File

The `linux touch -r` option allows you to set a file's timestamp to match that of another file (a reference file). This is useful for synchronizing timestamps across related files.

*\# Set file2.txt's timestamp to match file1.txt's timestamp*
`touch -r file1.txt file2.txt`

### Setting a Specific Date

With the `touch -d` option, you can set a file's timestamp to a specified date and time. The `touch -d linux` functionality accepts various string formats for the date.

*\# Set the timestamp to a specific date and time*
`touch -d "2023-01-01 12:30:00" nameofnewfile`

# 6. `file`

In the previous lesson, we learned about `touch`. Let's revisit that for a moment. Did you notice that the filename didn't conform to standard naming conventions, like you've probably seen with other operating systems such as Windows? Normally, you would expect a file called `banana.jpeg` to be a JPEG picture file. 

In Linux, filenames aren't required to represent the contents of the file. You can create a file called `funny.gif` that isn't actually a GIF.

To find out what kind of file a file is, you can use the `file` command. It will show you a description of the file's contents.

`file banana.jpg`

# 7. `cat`

After learning to navigate the filesystem, the next step is to view the contents of files. A fundamental and versatile tool for this is the `linux cat command`. The name `cat` is short for "concatenate", which hints at its ability to link files together.

## Viewing File Contents

The most basic use of the `cat` command is to display the content of a single file directly in your terminal.

`cat myfile.txt`

This command will print the entire content of `myfile.txt` to the screen. While this is perfect for short configuration files or text snippets, it's not ideal for viewing large files, as the text will scroll by very quickly. We will cover tools better suited for large files in a later lesson.

### Concatenating Files

True to its name, `cat` can combine, or concatenate, multiple files and display their combined output. The `cat linux` utility reads the files in the order they are provided and prints them sequentially.

`cat dogfile birdfile`

This command will first display the contents of `dogfile`, immediately followed by the contents of `birdfile`.

### Creating Files with Redirection

You can also use `cat` with the output redirection operator (`>`) to create new files. The `linux cat >` combination is a quick way to write text into a file directly from your terminal.

`cat > newfile.txt`

After running this command, you can type your text. Press `ctrl+D` on a new line to save and exit. This will create `newfile.txt` with the text you entered. 

> [!warning] **Be Careful**
> Using `>` on an existing file will overwrite it completely!

### Common cat Command Options

The `cat` command has several options to modify its behavior. Here are a couple of common ones:

- `-n`: This option numbers all output lines, starting from 1
- `-b`: This option numbers only the non-empty output lines

> [!info] **For a complete list of functionalities**
> You can always refer to the `cat manual linux` page by typing `man cat` in your terminal.

# 8. `less`

When viewing text files that are too large to fit on a single screen, the `less command` is an invaluable tool. As the old Unix saying goes, "less is more" (This is a play on the fact that there is also a `more` command with similar functionality). The `less` utility displays text in a paged format, allowing you to navigate through a file page by page without loading the entire file into memory.

## Getting Started with the Less Command

To start viewing a file, simply use the `command less` followed by the filename. This will open the file in the `less` interface.

`less /home/pete/Documents/text1`

## Navigation and Controls

You can use several keys to move through the document:

- **Arrow Keys and Page Keys**: Use `Page Up`, `Page Down`, `Up`, and `Down` to navigate line by line or page by page.
- **Go to Start**: Press `g` to move directly to the beginning of the text file.
- **Go to End**: Press `G` (Shift+g) to jump to the end of the text file.
- **Help Menu**: If you forget the commands while inside `less`, just press `h` to display a helpful summary.

## Unix Less Search

A powerful feature of `less` is its ability to search for text. To perform a `unix less search`, type `/` followed by the text you want to find, and then press Enter. This will highlight all occurrences of your search term.
- `/search_term` Searches forward for "search_term"
- `?search_term` Searches backward for "search-term"
- `n` Jumps to the next occurrence of the search term
- `N` Jumps to the previous occurrence

## How to Exit Less

When you are finished viewing the file, you need to know how to `exit less` and return to your command prompt.

- **Quit**: simply press `q` to quit the `less` viewer and go back to your shell.


# 9. `history`

Your shell keeps a record of the commands you've previously entered. You can access this list, which is incredibly useful when you want to find and reuse a command without retyping it. The `history` command is a fundamental tool in most Unix and Linux environments.

## Viewing your Command History

To see the list of commands you have used, simply type the `history` command. This feature provides a detailed log of your activity, making it easy to track your `history in linux`.

`history`

## Re-Running Previous Commands

The shell provides several shortcuts to make re-running commands easier.

- **Up Arrow**: Want to run the same command you just did? Just press the up arrow key to cycle backward through your history.
- **The `!!` Shortcut**: To execute the most recent command again, you can use `!!`. For example, if you just ran `cat file1`, typing `!!` and pressing Enter will run `cat file1` again.

## Searching your History

One of the most powerful history shortcuts is `ctrl-R`. This initiates a reverse search. After pressing `Ctrl-R`, start typing any part of the command you're looking for, and the shell will display the most recent match. You can press `Ctrl-R` repeatedly to cycle through older matches. Once you find the command you want, just press Enter to execute it.

## Managing the History List

Beyond just viewing your history, you can also manage it directly.

- **Clearing History**: If you want to clear the command history for your current session, you can use the  `history -c linux` command. This removes all entries from the history list in memory.
- **Writing to File**: To save the current session's history to your history file (usually `~/.bash_history`), you can use `history -w linux`. *This is useful for preserving commands before closing a session.*
- **Deleting a Specific Entry**: You can remove a single command from your history using `history -d <offset>`. The offset is the number shown next to the command in the `history` output. For example, `history -d 101` would delete the 101st entry. This is a key function of `history -d linux`.

> [!info] **Cluttered Terminal?**
> Use the `clear` command to wipe your display and start with a fresh screen!

# 10. `cp` (Copy)

The `cp` command is the standard tool for copying files and directories in Linux. Its basic syntax is `cp [SOURCE] [DESTINATION]`

## Basic File Copying

To copy a file, you specify the source file and the destination directory or path.

`cp myfile /home/pete/Documents/mydocs`

In this example, `myfile` is the source file, and `/home/pete/Documents/mydocs` is the destination directory. You can also copy a file and give it a new name in the destination

`cp myfile /home/pete/Documents/myfile_backup`

## Using Wildcards for Bulk Copying

Wildcards are special characters that help you select multiple files based on patterns, providing great flexibility.

- `*` Matches any sequence of characters
- `?` Matches any single character
- `[]` Matches any one of the characters enclosed in the brackets

For example, to copy all JPEG images from your current location to the `Pictures` directory:

`cp *.jpg /home/pete/Pictures`

## Copying Directories Recursively

If you try to copy a directory using `cp` without any options, you will receive an error. To copy a directory and all of its contents, including subdirectories, you must use the `-r` (recursive) flag.

`cp -r Pumpkin/ /home/pete/Documents`

This command copies the `Pumpkin` directory and everything inside it to your `Documents` directory.

## Handling File Overwrites

By default, `cp` will overwrite a file at the destination if it has the same name. To prevent accidental data loss, use the `-i` (interactive) flag, which prompts for confirmation before overwriting.

`cp -i myfile /home/pete/Pictures`

Conversely, if you want to force an overwrite without any prompts, you can use the `cp -f flag`. This is useful in scripts where user interaction is not possible.

`cp -f myfile /home/pete/Pictures`

## Preserving File Attributes with cp -p

When you copy a file, its metadata, such as modification time and ownership, is typically updated. To preserve these original attributes, the `cp -p` flag is essential. Using `cp -p in linux` ensures that the copy is an exact replica, not just in content but also in its metadata.

The `cp -p flag` is particularly useful for backups or when migrating files where preserving timestamps is critical.

`cp -p myfile /home/pete/backups/`

# 11. `mv` (Move)

The `mv` command, short for "move", is a fundamental utility in any Linux environment. It serves two primary purposes: renaming files or directories and moving them to a different location. Its functionality is similar in many ways to the `cp` command.

## Renaming Files and Directories

One of the most common uses of the `mv command in linux` is for renaming. The syntax is straightforward: you specify the old name and the new name. 

To rename a file:

`mv oldfile newfile`

This same logic applies to renaming directories:

`mv old_directory_name new_directory_name`

## Moving Files and Directories

The other core function of the `mv` command is to move items from one location to another.

To move a single file into a different directory:

`mv file2 /home/pete/Documents`

You can also move multiple files at once. Simply list all the source files followed by the target directory:

`mv file_1 file_2 /somedirectory`

A useful option for this is `linux mv -t`, which allows you to specify the target directory first. This can be clearer when moving many files.

`mv -t /somedirectory file_1 file_2`

Unlike the `cp` command, you do not need a `-r` flag to move a directory. The `bash mv` command handles directories by default. While some users search for `mv -r linux`, this option is not necessary for moving directories with `mv`.

## Important Options for the `mv` Command

By default, if you move a file to a destination where a file with the same name already exists, `mv` will overwrite it without warning. To prevent accidental data loss, you can use the following options:

- **-i (interactive)**: This is a crucial safety feature. It will prompt you for confirmation before overwriting any existing file.
`mv -i source_file destination_directory`

- **-b (backup)**: If you intend to overwrite a file but want to keep the old version, this option creates a backup of the destination file. The backup is typically renamed with a tilde (`~`) suffix.
`mv -b file1 directory_with_file1`

- **-v (verbose)**: This option makes the `mv` command print out what it is doing, showing each file being moved or renamed.
`mv -v file1 file2 /somedirectory`

# 12. `mkdir` (Make Directory)

As you work with files, you'll need to organize them into directories. The primary tool for this task is the `mkdir` command, which stands for "Make Directory". This command allows you to **create a directory in Linux** right from your terminal or command prompt.

## Creating a Single Directory

The most basic use of the `mkdir command in linux` is to create a single new directory. If the directory doesn't already exist, this command will create it in your current location. For example, to create a directory named `documents`:

`mkdir documents`

## Creating Multiple Directories

You can also create several directories at once by listing their names, separated by spaces. This is an efficient way to set up multiple folders quickly.

`mkdir books paintings`

## Creating Nested Directories

Sometimes you need to create a directory and its parent directories simultaneously. The `-p` (parent) option is perfect for this. This powerful feature of the `create folder linux command` prevents errors if parent directories don't exist. For instance, to create the directory `favorites` inside `hemmindway`, which is inside `books`:

`mkdir -p books/hemingway/favorites`

This single command creates `books`, `hemingway`, and `favorites` if they don't already exist, demonstrating a key capability when you need to create a directory in Linux.


# 13. `rm` (Remove)

In Linux, it's common to accumulate files that are no longer needed. To delete them, you use the `rm` (remove) command, a fundamental utility for managing your filesystem.

`rm file1`

## Understanding the Linux `rm` Command

The `linux rm command` is a powerful tool for deleting files and directories. However, its power comes with a significant risk. Unlike graphical operating systems, Linux does not have a recycle bin or trash can for command-line deletions. Once you use `rm`, the files are permanently gone.

## The Dangers of `rm -rf linux`

You must be extremely cautious when using `rm`. This is especially true for the `rm -rf linux` command combination, which can recursively and forcefully delete files without any confirmation prompts. A small typo with this command could lead to catastrophic data loss.

By default, some safety measures exist. For example, if you try to remove a write-protected file, the system will prompt you for confirmation before proceeding.

## Forceful Deletion with `-f`

To bypass these safety prompts and remove files unconditionally, you can use the force option.

`rm -f file1`

The `-f` (force) option tells `rm` to remove all specified files without prompting, even if they are write-protected (assuming you have the necessary permissions). This option is a key part of the `rm -rf linux command` and should be used with great care.

## Interactive Deletion with `-i`

For a safer approach, use the interactive flag. This is a highly recommended practice when working with the `rm linux` command.

`rm -i file1`

The `-i` (interactive) flag prompts you for confirmation before deleting each file, helping to prevent accidental removal.

## Removing Directories

By default, `rm` cannot delete a directory. To do so, you must use the recursive option.

`rm -r directory`

The `-r` (recursive) flag instructs `rm` to delete a directory and all of its contents, including any subdirectories and files. This is the 'r' in the `linus rm -rf` command.

## Using rmdir for Empty Directories

As a safer alternative, you can remove an empty directory with the `rmdir` command.

`rmdir directory`

The `rmdir` command will only succeed if the directory is completely empty, making it a safer choice than `rm -r` for cleanup tasks.

# 14. `find`

With countless files on a system, it can be challenging to locate a specific one. Fortunately, there's a powerful utility we can use for that: the `find` command. This tool is essential for efficient file management.

## Using the Find Command Line

The basic syntax for the `find command line` is `find [path] [expression]`. You must specify the directory to search in and the criteria for what you're looking for.

For example, to search for a file named `puppies.jpg` within the `/home` directory and all its subdirectories, you would use:

`find /home -name puppies.jpg`

The `find command in linux` is highly flexible, allowing for many different search expressions.

## Searching by Name and Type

One of the most common uses of the `find command` is searching by filename. As seen above, the `-name` option allows you to specify the exact name of the file you want to find. 

You can also specify the type of item you are searching for. The `-type` option is used for this purpose. For instance, if you want to find a directory instead of a file, you can use `d`.

`find /home -type d -name MyFolder`

In this command, we set the type to `d` for directory and are searching for an item named `MyFolder`. To search specifically for regular files, you would use `-type f`.

## Recursive Searching

A key feature of the `find command linux` users appreciate is its recursive nature. When you specify a starting directory, `find` doesn't just look in that single directory; it automatically searches through all subdirectories contained within it. This makes it an incredibly thorough tool for locating items anywhere in a directory tree.

# 15. `help`

When working on the Linux command line, you'll often need a quick reminder of how a command works or what options it accepts. Fortunately, Linux provides excellent tools for command line help right in the terminal.

## The 'help' Command for Bash Built-ins

One of the most direct tools is `help`, a command that is built directly into the Bash shell. It is specifically designed to provide enough information about other Bash built-in commands. A built-in command is part of the shell itself, not a separate program. Examples include `echo`, `cd`, and `pwd`.

To use the **Linux help command**, simply type `help` followed by the name of the built-in command.

`help echo`

This will display a summary of the `echo` command, its syntax, and a list of available options. This is the fastest way to get assistance for shell-specific functions.

## The --help Flag for Executable Programs

For most other executable programs that are not built into the shell, the `help` command won't work. Instead, a common convention is to provide a `--help` flag. This option signals the program to print a usage summary and then exit.

`ls --help`

While most developers adhere to this standard, it's not universal. However, trying the `--help` flag is usually the best first step to find help for an unfamiliar program. It's a fundamental skill for anyone learning about **Linux Commands**.


# 16. `man`

In Linux, nearly every command comes with its own instruction manual. These are called "man pages" (short for manual pages), and they are an essential resource for learning how to use the system effectively.

## Understanding man Pages

man pages are the built-in documentation for Linux commands, utilities, and system calls. They provide a detailed description of what a command does, its available options (or flags), and how to use it. They are your first and best source for command-line help.

## Accessing a Manual with man

To view the manual for any command, you can use the `man` command itself, followed by the name of the command you want to learn about. For example, to read the manual for the `ls` command, you would type:

`man ls`

This will open the `ls man` page, a comprehensive document detailing all of its features. You can scroll through the manual using the arrow keys and press `q` to quit and return to the command line.

## Finding Details on Command Options

man pages are particularly useful for understanding command options. For instance, if you've seen the `ls -l` command and want to know what the `-l` flag does or what each column in the output means, the `man ls` page provides a complete explanation. It's the definitive guide for any variations of a command, making it an indispensable tool.


# 17. `whatis`

As you explore the Linux command line, you'll encounter a vast number of commands. It's natural to forget what a specific command does. Fortunately, there's a simple utility to help you out.

## What is the `whatis` command in Linux?

The `whatis` command in Linux displays a concise, one-line description of a command directly from its manual (`man`) page. It's a quick way to get a reminder of a command's primary function without reading the entire `man page`. Think of the **Linux whatis** command as a quick dictionary for your terminal.

## How to Use the `whatis` Command

Using the `whatis command in linux` is straightforward. Simply type `whatis` followed by the name of the command you want to know about. For example, if you're unsure about the `cat` command, you can run:

`whatis cat`

This will return a short description, such as "cat - concatenate files and print on the standard output".

## Understanding the Output

The description provided by the **linux whatis command** is sourced directly from the NAME section of the command's `man page`. This ensures the information is accurate and consistent with the system's documentation. If a command has multiple `man pages` in different sections, `whatis` may display a line for each, helping you understand its various contexts.


# 18. `alias`

Typing long or repetitive commands can be tedious. Fortunately, you can create a shortcut, or a **Linux alias**, to make your command-line experience more efficient. The `alias` command lets you define a custom name for any command or sequence of commands.

## Creating a Temporary `alias`

To create a temporary `alias` that lasts for your current terminal session, you simply specify a name and set it equal to the command string.

For example, to create an alias named `ll` for the `ls -la` command, you would use the `alias command linux` syntax like this:

`alias ll='ls -la'`

Now, instead of typing `ls -la`, you can just type `ll` and it will execute the same command. This is a simple yet powerful way to customize your shell.

## Making an `alias` permanent

A temporary alias will disappear once you chose your terminal or reboot your system. To make a `command alias in linux` permanent, you need to add it to your shell's configuration file. For the Bash shell, this file is typically `~/.bashrc`.

1. Open the file in a text editor: `nano ~/.bashrc`
2. Add your alias definition to the file, just as you typed it on the command line:
`alias ll='ls -la'`
`alias update='sudo apt update && sudo apt upgrade'`
3. Save the file and exit the editor.

For the changes to take effect, you must either close and reopen your terminal or tell the shell to reload the configuration file using the `source` command:

`source ~/.bashrc`

Your **Linux command alias** will now be available every time you start a new terminal session.

## Removing an `alias`

If you no longer need an alias, you can remove it with the `unalias` command. This will remove it from your current session.

`unalias ll`

To remove a permanent alias, you must also delete its definition from your `~/.bashrc` file.


# 19. `exit`

## The Exit Command

The most common way to end a shell session is with the `exit` command. When you type `exit` and press Enter, the current shell process terminates. This is a universal command that works in virtually any shell environment, making it a fundamental part of any beginner Linux tutorial.

`exit`

## The Logout Command

Another command you can use for a terminal exit is `logout`. This command is specifically designed to terminate a login shell. While in many modern systems it behaves similarly to `exit`, it's good practice to know both commands.

`logout`

## Closing the Terminal Window

If you are working within a **Graphical User Interface** (GUI), you also have the option to simply close the terminal window. This action typically sends a signal that terminates the shell session running inside it, providing a quick way to perform a terminal exit.