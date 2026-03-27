# 1. `stdout` (Standard Out)

As you continue to learn Linux, you've seen how commands produce output. This brings us to the important topic of I/O (input/output) streams, specifically standard output or `stdout`. Let's explore this concept by running the following command:

`echo Hello World > peanuts.txt`

After running this, you will find a new file named `peanuts.txt` in your current directory. If you view its contents, you'll see the text "Hello World".  Let's break down what happened.

## Understanding Standard Output (`stdout`)

First, consider the command without the special character:

`echo Hello World`

By default, many commands send their results to `stdout`, which is your terminal screen. This is why `echo Hello World` displays the text directly in your shell. Processes use I/O streams to receive input (standard input or `stdin`) and send output. I/O redirection allows us to change this default behavior, giving us greater control over our data.

## Redirecting `stdout` with `>`

The `>` character is a redirection operator. It intercepts the data heading to `stdout` and sends it to a new destination.

`>`

In our example, it sends the output of `echo Hello World` displays the text directly in your shell. Processes use I/O streams to receive input (standard input or `stdin`) and send output. I/O redirection allows us to change this default behavior, giving us greater control over our data.

## Appending `stdout` with `>>`

What if you want to add to a file without erasing its contents? For that, we use the `>>` operator.

`echo Hello World >> peanuts.txt`

This operator appends the output to the end of the specified file. If the file doesn't already exist, it will be created, just like the `>` operator. Mastering `stdout` redirection is a fundamental step in your Linux journey.

# 2. `stdin` (Standard In)

In our previous lesson, we learned about redirecting the standard output (`stdout`) stream. Similarly, we can also manage the standard input (`stdin`) stream. By default, a program receives its `stdin` and writes its results to `stdout`. Understanding how to control both `stdin` and `stdout` is crucial for effective command-line work.

## How to redirect `stdin`

Just as we use `>` for `stdout` redirection, we use the `<` operator to `redirect stdin`. This powerful feature allows you to tell a command to read its input from a file instead of waiting for you to type it on the keyboard. This is a core concept of input redirection.

## Practical Example with `cat stdin`

Let's revisit the `peanuts.txt` file from the previous lesson, which contains the text "Hello World". Consider the following command:

`cat < peanuts.txt > banana.txt`

Here's a breakdown of what happens:

1. The `< peanuts.txt` part tells the shell to `redirect stdin` for the `cat` command, making it read from `peanuts.txt` instead of the keyboard.
2. The `cat` command processes its input. In this case, using `cat stdin` means it reads the content of `peanuts.txt`.
3. The `> banana.txt` part redirects the standard output of `cat` to a new file named `banana.txt`.

Ultimately, the content of `peanuts.txt` is copied to `banana.txt`. This example effectively demonstrates how to manage both `stdin and stdout` in a single, efficient command.

# 3. `stderr` (Standard Error)

Let's explore what happens when a command produces an error. Try to list the contents of a directory that doesn't exist and redirect the output to a file named `peanuts.txt`.

`ls /fake/directory > peanuts.txt`

Instead of a clean prompt, you will see an error message on your screen:

`ls: cannot access /fake/directory: No such file or directory`

You might be wondering why this message wasn't sent to the file. This is because another I/O stream is at play: **standard error**, or `stderr`.

## What is Standard Error in Linux?

In Linux, `stderr` is a default output stream used by programs to send error messages and diagnostics. It is completely separate from the standard output (`stdout`) stream, which is used for normal program output. By default, both `stdout` and `stderr` send their output to your terminal screen, which is why you see the error message directly

To control `stderr`, you need a different redirection method.

## Understanding File Descriptors

To manage I/O streams like `stdin`, `stdout`, and `stderr`, the system uses file descriptors. A **file descriptor** is a non-negative number that the kernel uses to identify an open file or stream. The default file descriptors are:

- `0`: `stdin`
- `1`: `stdout`
- `2`: `stderr`

The number `2` is the dedicated `stderr file descriptor`, and we can use it to control where error messages go.

## Redirecting `stderr` to a File

To redirect `stderr` to a file, you use the file descriptor `2` followed by the `>` operator. This command will send any error messages into the specified `stderr file`.

`ls /fake/directory 2> peanuts.txt`

Now, your terminal will be quite, and the error message will be inside `peanuts.txt`

## Combining `stdout` and `stderr`

What if you want to capture both normal output and error messages in the same file? You can achieve this by redirecting both streams.

`ls /fake/directory /etc/passwd > peanuts.txt 2>&1`

Let's break this down:

1. `> peanuts.txt` redirects `stdout` (file descriptor 1) to the `peanuts.txt` file.
2. `2>&1` redirects `stderr` (file descriptor 2) to the same location that `stdout` (file descriptor 1) is currently pointing to.

The order is important. `2>&1` sends `stderr` to the current destination of `stdout`. In this case, `stdout` is pointing to a file, so `stderr` is also sent to that file.

A more modern and shorter way to redirect both `stdout` and `stderr` is by using `&>`.

`ls /fake/directory /etc/passwd &> peanuts.txt`

## Discarding Error Messages

Sometimes, you might want to run a command and completely ignore any potential error messages. To do this, you can redirect `stderr` to a special file called `/dev/null`, which discards any data written to it.

`ls /fake/directory 2> /dev/null`

This command will execute, and any error output from `stderr` will be sent to `/dev/null` and discarded, leaving your screen clean.


# 4. pipe and tee

In Linux, the command line becomes incredibly powerful when you start connecting commands. Instead of running one command, saving its output, and then running another, you can create a pipeline to pass data directly between them.

## Understanding the Pipe Operator

Let's start with a command that produces a lot of output:

`ls -la /etc`

The list of items is likely too long to fit on your screen, making it difficult to read. While you could redirect this output to a file, a more efficient method is to send it directly to another command, like `less`, for easy viewing.

`.s -la /etc | less`

The pipe operator `|`, represented as a vertical bar, is the key to this process. It takes the standard output (`stdout`) of the command on its left and uses it as the standard input (`stdin`) for the command on its right. In this case, we *piped* the output of `ls -la /etc` directly into the `less` command. The pipe is a fundamental tool you will use constantly.

## Splitting Output with the Tee Command

What if you want to see the output on your screen *and* save it to a file simultaneously? This is where the `tee` command comes in. The `pipe and tee command in linux` is a classic combination for logging and monitoring.

`ls | tee peanuts.txt`

After running this, you will see the output of `ls` on your terminal. If you also check the contents of `peanuts.txt`, you will find the exact same information. The `tee` command effectively splits the output stream into two directions: one to standard output and one to a specified file.

## Combining Pipe and Tee

You can create even more advanced workflows by chaining these commands. A common patter is to `pipe to tee` in the middle of a longer command chain. This allows you to save an intermediate result while continuing to process the data.

For example, you can use the `linux pipe tee` combination to view and save output before further filtering:

`ls -la /etc | tee etc_listing.txt | grep "conf"`

This command does three things:

1. It lists the contents of the `/etc` directory.
2. It pipes that output to `tee`, which saves a copy to `etc_listing.txt` and also passes it along.
3. The output from `tee` is then piped to `grep`, which filters for lines containing "conf".

# 5. `env` (Environment)

Your Linux system uses environment variables to store information that the shell and other processes can access. These variables contain useful data about your user session and system configuration.

## Exploring Basic Environment Variables

 You can view the value of a specific variable by prefixing its name with a `$` symbol. For example, run the following command:

`echo $HOME`

This command will display the path to your home directory, which might look something like `/home/pete`.

Now, try another one:

`echo $USER`

This will output your current username. But where does this information come from? It's stored in your shell's environment.

## What Does `env` Do in Linux?

To see all the environment variables currently set for your session, you can use the `env` command. The `linux env command` is a fundamental tool for inspecting your shell's configuration.

`env`

Running the `env` command will output a list of key-value pairs. Here is a short example of what you might see:

`PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/bin`
`PWD=/home/user`
`USER=pete`

## The Importance of the PATH variable

One of the most important variables in your `env linux` output is `PATH`. You can view its contents specifically with:

`echo $PATH`

This command returns a colon-separated list of directories. When you type a command, your system searches through these directories to find the corresponding executable file.

Imagine you manually install a program in a non-standard directory like `/pot/coolapp/bin`. If you try to run it by typing `coolcommand`, you might get a "command not found" error. This happens because the directory containing your program is not listed in the `PATH` variable, so the shell doesn't know where to look for it.

To fix this, you can modify the `PATH` variable to include the new directory. By adding your custom directory to `PATH`, you enable the shell to find and execute your programs from anywhere in the terminal.

## Setting an Environment Variable for the Current Session

Running the following command in your terminal sets the envionment variable `TEST` for the current session only:

`export TEST=test`

After this, if you run:

`echo $TEST`

The output will be 

`test`

This variable will be available as long as the terminal session remains open. Once you close and reopen the terminal, the variable will no longer exist.

## Making the Environment Variable Persistent Across Sessions

If you want the environment variable to be available in every terminal session (even after closing and reopening the terminal), you need to add it to your shell's startup file. In the case of Bash (the default shell for many Linux distributions and macOS), this file is usually `.bashrc` in your home directory.

1. Open `.bashrc` in your preferred text editor. For example:

`nano ~/.bashrc`

2. Add the `export` line to the end of the file:

`export TEST=test`

3. Save and exit the editor (in Nano, this would be `Ctrl+X` then `Y` to confirm, and `Enter`).
4. To apply the changes immediately without reopening the terminal, run:

`source ~/.bashrc`

After this, the `TEST` variable will be available in all future terminal session, and running `echo $TEST` will print `test` even after you close and reopen the terminal.

## A Note on Shell Configuration Files

- For **Bash** (the default on many systems), the relevant file is `~/.bashrc` for non-login interactive shells.
- For **Zsh**, the equivalent file is usually `~/.zshrc`.
- For **Fish**, you'd typically use `~/.config/fish/config.fish`.

# 6. `cut`

We're going to learn a couple of useful commands for processing text. Before we begin, let's create a file to work with. Copy and past the following command. After pasting, you will need to add a literal TAB character between "lazy" and "dog" (you can often do this by pressing `Ctrl+V` then `TAB`).

`echo 'The quick brown; fox jumps over the laxy dog' > sample.txt`

The first command we'll explore is `cut`, which extracts portions of text from a file.

## Cutting by Character

You can extract content based on character position using the `-c` flag.

`cut -c 5 sample.txt`

This command outputs the 5th character from each line of the file. In our case, the output is "q". Note that spaces also count as characters.

## Cutting by Field with `cut f`

A more powerful feature is cutting by fields. The `cut f` syntax, using the `-f` flag, allows you to extract text based on field position. By default, `cut` uses the TAB character as a delimiter, meaning everything separated by a TAB is considered a distinct field.

Let's see how to cut f based on fields:

`cut -f 2 sample.txt`

Since we inserted a TAB between "lazy" and "dog", this command treats "dog" as the second field. Your output should be "dog".

## Using Custom Delimiters

You can also combine the field flag with the delimiter flag (`-d`) to specify a custom delimiter. This is useful when working with files that use characters like commas or semicolons to separate data.

`cut -f 1 -d ";" sample.txt`

This command changes the delimiter from a TAB to a semicolon (`;`). Since we are cutting the first field (`-f 1`), the result will be "The quick brown".

# 7. `paste`

The `paste` command is similar to the `cat` command; it merges lines together in a file. Let's create a new file with the following contents:

`sample2.txt`
`The`
`quick`
`brown`
`fox`

Let's combine all these lines into one line:

`paste -s sample2.txt`

The default delimiter for `paste` is TAB, so now there is one line with TABs separating each word. 

Let's change this delimiter (`-d`) to something a little more readable:

`paste -d ' ' -s sample2.txt`

Now everything should be on one line delimited by spaces.

# 8. `head`

In Linux, you often need to inspect the contents of very large files, such as system logs. For example, if you run `cat /var/log/syslog`, you'll see pages of text scroll by, making it difficult to get a quick overview. So, what if you only want to **view the beginning of a file**? The `head` command is the perfect tool for this job.

## Default Behavior of the `head` Command

By default, the `head` command displays the first 10 lines of any given file. This is a fundamental part of our **beginner Linux guide** for handling text. To see it in action, simply provide a filename as an argument:

`head /var/log/syslog`

This command will output the first 10 lines from `/var/log/syslog`, allowing you to quickly check the file's initial content without opening it in an editor. 

## Customizing the Line Count

The **Linux head** command is flexible. You can easily change the number of lines it displays using the `-n` flag, which stands for "number of lines". For instance, if you want to see the first 15 lines of a file, you would use the `head -n` option like this:

`head -n 15 /var/log/syslog`

This makes `head` one of the most useful **Linux commands** for quickly inspecting file headers or log entries.


# 9. `tail`

The `tail` command is a fundamental utility for anyone learning Linux. As its name suggests, it allows you to view the "tail" or end of a file. This is particularly useful for checking the most recent entries in rapidly changing files, such as system logs.

## Viewing the End of a File

By default, the `tail` command displays the last 10 lines of a specified file. It functions as the counterpart to the `head` command.

`tail /var/log/syslog`

Just like with `head`, you can customize the number of lines you want to see by using the `-n` option. For example, to see the last 20 lines, you would use the following command:

`tail -n 20 /var/log/syslog`

This flexibility makes the `Linux tail` command an essential tool for quickly inspecting file endings without opening the entire file.

## Real-Time File Monitoring with `tail -f`

One of the most powerful features of the `tail` command is its ability to monitor files in real-time. This is achieved with the `-f` (follow) flag. When you use `tail -f`, the command doesn't exit after displaying the last few lines. Instead, it waits for new data to be appended to the file and prints it to the screen as it arrives.

`tail -f /var/log/syslog`

Try running this command. As you continue to use your system, you will see new lines appear in your terminal. This makes `tail -f` an indispensable tool for system administrators and developers who need to `view logs` and monitor application output as it happens.


# 10. `expand and unexpand`

Inconsistent spacing can make text files difficult to read. While tabs are meant to create uniform indentation, their display width can vary across different editors and systems. This can disrupt text formatting and alignment. Fortunately, Linux provides simple tools to manage this by converting between tabs and spaces.

## Converting Tabs to Spaces with the `expand` Command

When you need to ensure consistent spacing, you can convert tabs into a standard number of spaces using the `expand` command. This command reads a file and replaces each tab character with a set of space characters, printing the result to standard output.

`expand sample.txt`

By default, the `expand command` converts each tab into 8 spaces. This simple utility is a powerful tool for improving text formatting.

## Saving the Converted Output

The `expand` command only prints the converted text to your terminal. To save the changes, you must redirect the output to a new file.

`expand sample.txt > result.txt`

This command takes the output of `expand sample.txt` and writes it into `result.txt`, giving you a new file with spaces instead of tabs.

## Converting Spaces to Tabs with the `unexpand` Command

The reverse operation, converting spaces back into tabs, is handled by the `unexpand` command. This can be useful for reducing file size or adhering to coding standards that require tabs.

`unexpand -a result.txt`

By default, `unexpand` only converts leading spaces on each line. The `-a` option tells the `unexpand command` to convert all instances of 8 spaces into a tab, not just those at the beginning of a line, providing more comprehensive control over your Linux spaces and tabs.

# 11. `join and split`

In Linux, managing and manipulating text files is a common task. Two powerful utilities for this are `join` and `split`. The `join` command merges lines from two files based on a common field, while `split` breaks a large file into smaller, more manageable pieces.

## Joining Files by a Common Field

The `join` command is a fundamental tool when you need to **linux join files**. By default, it combines lines from two sorted files based on an identical first field.

For example, imagine you have two files you want to merge:

`file1.txt`
`1 John`
`2 Jane`
`3 Mary`

`file2.txt`
`1 Doe`
`2 Doe`
`3 Sue`

Using the `join` command, you can combine them easily:

`$ join file1.txt file2.txt`
`1 John Doe`
`2 Jane Doe`
`3 Mary Sue`

As you can see, the files were joined using the common first field (1, 2, 3). for `join` to work correctly, the join fields in both files must be sorted.

## Specifying Different Join Fields

What if the common field is not the first column? You can tell `join` which fields to use. Consider these files:

`file1.txt`
`John 1`
`Jane 2`
`Mary 3`

`file2.txt`
`1 Doe`
`2 Doe`
`3 Sue`

Here, we need to join on the second field of `file1.txt` and the first field of `file2.txt` The command would be:

`$ join -1 2 -2 1 file1.txt file2.txt`
`1 John Doe`
`2 Jane Doe`
`3 Mary Sue`

The `-1 2` flag specifies field 2 of the first file, and `-2 1` specifies field 1 of the second file.

## Splitting Large Files

The `split` command does the opposite of joining; it divides a large file into smaller ones.

`split somefile`

By default, this command splits `somefile` into new files once a 1000-line limit is reached. The output files are named `xaa`, `xab`, and so on. You can customize this behavior, for example, by specifying a different line count with the `-l` flag or splitting by file size with the `-b` tag.

# 12. `sort`

The `sort` command is useful for sorting lines.

`file1.txt
`dog`
`cow`
`cat
`elephant
`bird`

`$ sort file1.txt
`bird
`cat
`cow
`dog
`elephant`

You can also do a reverse sort:

`$ sort -r file1.txt`
`elephant`
`dog`
`cow`
`cat`
`bird`

And also sort by numerical value:

`$ sort -n file1.txt`
`bird`
`cat`
`cow`
`elephant
`dog`


# 13. `tr` (Translate)

The `tr` command, short for translate, is a command-line utility in Linux that translates or deletes characters from standard input. It is a useful tool for simple text manipulation and is often used with pipes to process the output of other commands. The `trtranslate` functionality is a core part of text processing.

## Basic Character Translation

The most common use of `tr` is to substitute one set of characters for another. For example, you can easily translate all lowercase characters to uppercase.

```bash
$ echo "hello world" | tr a-z A-Z
HELLO WORLD
```

In this example, we piped the output of `echo` to the `tr` command. The `tr` command then translated the character range `a-z` into the corresponding characters in the range `A-Z`.

### Deleting Characters with -d

Another powerful feature is the ability to delete specific characters using the `-d` (delete) option. This is particularly useful for cleaning up text. For instance, if you want to remove all digits from a string, you can use `linux tr -d`.

```bash
$ echo "My address is 123 Main Street" | tr -d '0-9'
My address is  Main Street
```

Here, the `tr -d` command deleted every character in the specified set ('0' through '9') from the input stream. This is a common pattern for `tr -d linux` users.

### Squeezing Repeated Characters

The `tr` command can also "squeeze" repeated characters into a single instance using the `-s` (squeeze) option. This is great for normalizing text with extra whitespace.

```bash
$ echo "Hello      World,   how   are   you?" | tr -s ' '
Hello World, how are you?
```

In this case, `tr -s ' '` replaced sequences of multiple spaces with a single space, making the output much cleaner.


# 14. `uniq` (Unique)

The `uniq` (unique) command is an essential tool for text processing in Linux. It helps you filter and manage duplicate lines within a text file, but it's important to understand how it works to use it effectively.

### Basic Duplicate Removal

The primary function of the `uniq` command is to remove duplicate adjacent lines. Imagine you have a file named `reading.txt` with the following content:

```plaintext
book
book
paper
paper
article
article
magazine
```

To remove the repeated lines, you can run the `uniq` command:

```bash
$ uniq reading.txt
book
paper
article
magazine
```

As you can see, `uniq` outputs a version of the file with the duplicate adjacent lines removed.

### Advanced Filtering Options

The `uniq` command also provides several options for more detailed analysis.

To count the occurrences of each line, use the `-c` (count) flag:

```bash
$ uniq -c reading.txt
      2 book
      2 paper
      2 article
      1 magazine
```

To display only the lines that are not repeated (i.e., are unique), use the `-u` (unique) flag:

```bash
$ uniq -u reading.txt
magazine
```

Conversely, to display only the lines that are repeated, use the `-d` (duplicated) flag:

```bash
$ uniq -d reading.txt
book
paper
article
```

### The Importance of Sorting

A critical detail about the **uniq linux** command is that it only detects duplicate lines if they are directly adjacent to each other. If the duplicates are scattered throughout the file, `uniq` will not identify them.

Consider this version of `reading.txt` where duplicates are not adjacent:

```plaintext
book
paper
book
paper
article
magazine
article
```

Running `uniq` on this file will produce a surprising result:

```bash
$ uniq reading.txt
book
paper
book
paper
article
magazine
article
```

No lines were removed because no two identical lines were next to each other. To solve this, you must first sort the file's contents. By piping the output of `sort` into `uniq`, you ensure that all identical lines become adjacent, allowing `uniq` to work correctly. This combination is a powerful and common pattern in shell scripting.

```bash
$ sort reading.txt | uniq
article
book
magazine
paper
```

This command first sorts the lines alphabetically, then `uniq` filters out the duplicates, giving you a clean list of unique entries.


# 15. `wc and nl`

In Linux, analyzing text files is a common task. Two fundamental utilities for this are `wc` and `nl`, which help you count content and number lines, respectively.

### Counting with the wc Command

The `wc` (word count) command is a powerful tool for basic file analysis. When run on a file, it provides a summary of its contents.

```bash
$ wc /etc/passwd
 96     265    5925 /etc/passwd
```

The output displays three numbers followed by the filename. From left to right, these numbers represent:

1. The number of lines.
2. The number of words (the Linux word count).
3. The number of bytes.

### Getting Specific Counts

Often, you only need one piece of information. You can use options to display a specific count instead of all three.

- `-l`: Shows only the line count.
- `-w`: Shows only the word count.
- `-c`: Shows only the byte count.

For example, to see just the number of lines in the `/etc/passwd` file, you would use:

```bash
$ wc -l /etc/passwd
96
```

### Numbering Lines with the nl Command

Another useful command for inspecting files is `nl` (number lines). As its name suggests, it reads a file and outputs its content with line numbers added to the beginning of each line. This is especially helpful for reviewing scripts or configuration files.

Consider a file named `file1.txt` with the following content:

```plaintext
i
like
turtles
```

Using the `nl` command, you can easily add Linux line numbers:

```bash
$ nl file1.txt
     1 i
     2 like
     3 turtles
```

Both `wc` and `nl` are essential commands for everyday text processing on the Linux command line.


# 16. `grep`

The `grep` command is arguably the most essential text-processing tool you will use in a Linux environment. It allows you to search through files or streams of data for lines that match a specific pattern. Instead of manually digging through countless lines of text to find a specific string or configuration, you can simply use `grep` to do the heavy lifting.

### Basic Grep Usage

At its core, `grep` searches for a pattern within a file. Let's use a file named `sample.txt` as an example. To find all lines containing the word "fox", you would run:

```bash
grep fox sample.txt
```

The output will display every line from `sample.txt` where "fox" is found.

### Advanced Pattern Matching with grep -e

For more complex searches, the `grep -e command` is incredibly useful. The `-e` flag explicitly tells `grep` that the next argument is the pattern. This is particularly helpful when searching for patterns that start with a hyphen (`-`), which might otherwise be misinterpreted as an option.

Here is a `grep -e example` where we search for the string "-v" in a file:

```bash
grep -e "-v" /path/to/some/file.conf
```

Without `-e`, `grep` would treat `-v` as the "invert match" option. The `grep -e command` ensures your pattern is always interpreted correctly.

### Useful Grep Flags

You can modify `grep`'s behavior with various flags to refine your search results.

- **Case-Insensitive Search**: Use the `-i` flag to make your search case-insensitive.
    
    ```bash
    grep -i somepattern somefile
    ```
    
- **Count Matching Lines**: To count how many lines match your pattern instead of displaying them, use the `grep -c` flag.
    
    ```bash
    grep -c fox sample.txt
    ```
    
- **Show Only the Match**: If you only want to see the exact part of the line that matches the pattern, use the `grep -o` flag.
    
    ```bash
    grep -o fox sample.txt
    ```
    
- **Search for Patterns from a File**: When you have multiple patterns to search for, you can list them in a file and use the `grep -f` flag to tell `grep` to use that file for patterns.
    
    ```bash
    grep -f patterns.txt sample.txt
    ```
    

### Combining Grep with Other Commands

The true power of `grep` is unlocked when you combine it with other commands using pipes (`|`). This allows you to filter the output of any command.

For instance, you can filter environment variables to find ones related to the user:

```bash
env | grep -i User
```

You can also use `grep` with regular expressions to perform more sophisticated pattern matching. For example, to find all files ending with `.txt` in a directory:

```bash
ls /somedir | grep '.txt$'
```

As you can see, `grep` is a versatile and powerful tool for any Linux user.