
# 1. Users and Groups

In any multi-user operating system, managing users and groups is a fundamental concept. This is a core part of the **basics of linux**, designed for access control and permissions. When a process runs, it does so as the user who started it. Likewise, file access and ownership are dependent on permissions, preventing one user from accessing another's private documents.

### The Basics of Linux Users and Groups

Every user on a Linux system is assigned a personal home directory, typically located at `/home/username`. This directory is where their user-specific files and configurations are stored, though the exact path can vary between Linux distributions.

The system identifies users with a User ID (UID) and groups with a Group ID (GID). While we use human-readable usernames, the operating system relies on these unique numerical IDs for all permission-related tasks. Groups are simply collections of users, making it easier to manage permissions for multiple accounts at once.

### The Superuser and the Sudo Command

Within the hierarchy of **linux users and groups**, one user stands above all others: `root`, also known as the superuser. The `root` user has unlimited power, capable of accessing any file and managing any process. Operating as `root` continuously is risky, as a simple mistake could damage the system.

To mitigate this risk, authorized users can execute commands with root privileges using the `sudo` (superuser do) command. This allows for administrative tasks without logging in as the `root` user. Understanding how to properly use `sudo` is essential for anyone seeking the `quickest way to linux advanced` administration skills.

Let's try to view a protected file, such as `/etc/shadow`, which stores encrypted user passwords.

```bash
cat /etc/shadow
```

You will receive a "Permission denied" error. Let's examine the file's permissions:

```bash
$ ls -la /etc/shadow

-rw-r----- 1 root shadow 1134 Dec 1 11:45 /etc/shadow
```

While we will cover permissions in detail later, this output shows that only the `root` user and members of the `shadow` group can read this file. Now, run the command again with `sudo`:

```bash
sudo cat /etc/shadow
```

This time, you will be prompted for your password and, upon successful authentication, the contents of the file will be displayed.