
### Linux History

- 1969 - Ken Thompson & Dennis Ritchie create UNIX at Bell Labs
- 1973 - UNIX rewritten in C, making it portable and widely adopted
- 1983 - Richard Stallman launches the GNU Project (GNU != UNIX)
- 1985 - GNU General Public License (GPL) is introduced
- 1990 - GNU kernel "Hurd" remains incomplete
- 1991 - Linus Torvalds starts developing Linux kernel
- 1992 - Linux released under GPL - GNU/Linux ecosystem begins

### Choosing a Distribution

- A Linux system is divided into three main parts:
	- **Hardware** - This includes the physical components of your computer, i.e. CPU, Memory, Storage Devices, etc.
	- **Linux Kernel** - As the core of the operating system, the kernel manages the hardware and facilitates communication between software and hardware.
	- **User Space** - This is the environment where you, the user, interact with the system through applications and command-line interfaces.

#### What is a Linux Distribution?

A Linux distribution bundles the Linux kernel with a collection of software, such as system utilities, libraries, and applications. It often includes a package manager for installing and managing software, and a desktop environment for the graphical user interface (GUI). Essentially, a distro is a complete, ready-to-use operating system built around the kernel.

#### Key Factors When Choosing a Distro

- **Experience Level** - If you are new to Linux, look for beginner-friendly distros (i.e. Ubuntu, Mint, etc.)
- **Desktop Environment** - Defines the look & feel of the system. Popular options include GNOME, KDE Plasma, and KFCE. Different environments may support different display technologies like Wayland, which can be important for gaming, multi-monitor setups, or features like Variable Refresh Rate and HDR.
- **Package Management** - Distros use package managers to install, update, and remove software. The two main families are Debian-based (using apt and .deb files) and Red Hat-based (using dnt or yum and .rpm files). The availability of software can sometimes differ, though universal package formats like Flatpak and Snap are making it easier to install apps across different distros.
- **Community and Support** - A large, active community means more tutorials, forums, and documentation are available if you run into problems. Some distros also have strong commercial backing, which can translate to excellent official support.

### Debian

#### Getting Started with Debian

**Debian** is a highly influential operating system composed entirely of free and open-source software. With a development history spanning decades, it is one of the oldest and most respected community-driven projects. This lesson provides a great starting point for anyone interested in Debian getting started. Its commitment to software freedom and its robust, volunteer-based structure make it a unique and powerful choice.

- Stable, Testing, and Unstable branches do what they say on the tin.

#### Package Management

**Debian** uses its own powerful package management tools, primarily apt (Advanced Package Tool), to install, upgrade, and manage software. The system maintains a massive repository of pre-compiled software packages, ensuring that users can easily find and install everything from desktop applications to development tools like the *build essential debian* package. This robust system is a cornerstone of the **Debian** user experience.

#### Stability for Desktop and Enterprise Use

The **Debian** Stable branch is renowned for its rock-solid stability. While it may not always feature the absolute latest software, it is thoroughly tested and secure, making it a dependable "core" operating system. This reliability has made **Debian** a popular foundation for many other Linux distributions, including Ubuntu. Its performance and security also make it a strong candidate for **Debian enterprise Linux** environments, powering servers and critical infrastructure worldwide.


### Red Hat Enterprise Linux

#### What is Red Hat Enterprise Linux

Red Hat Enterprise Linux, often called RHEL, is a commercial Linux distribution developed by Red Hat for the corporate market. It is a leading choice for an enterprise Linux operating system, built to provide long-term stability, security, and professional support. While RHEL requires a subscription for use in production, Red Hat provides its source code freely, which forms the basis for other distributions.

#### Package Management with RPM

RHEL uses the RPM (Red Hat Package Manager) format for its software packages. For managing these packages, it provides high-level tools like YUM (Yellowdog Updater, Modifier) and its successor, DNF (Dandified YUM). This is a key difference from distributions like Debian or Ubuntu, which are sometimes used as debian enterprise linux alternatives and use the .deb package format with the ATP package manager.

#### The Enterprise Advantage

The primary appeal of RHEL lies in its suitability for *enterprise Linux systems*. It is designed for mission-critical workloads, offering a predictable release cycle, long-term support (up to 10 years or more), and a vast ecosystem of certified hardware and software. This makes it a reliable foundation for servers, cloud computing, and containerized applications in large-scale corporate environments.

#### RHEL and its Ecosystem

To understand RHEL's place, it's helpful to know its relationship with other distributions. Fedora serves as the upstream, community-driven project where new features are developed and tested. These innovations are then refined and stabilized for inclusion in future versions of RHEL. CentOS Stream now serves as the development branch for upcoming RHEL releases.

#### Professional Certification Path

For those looking to *learn Red Hat Enterprise Linux* professionally, Red Hat offers a well-respected *certification redhat* program. Key certifications include the Red Hat Certified System Administrator (RHCSA) and Red Hat Certified Engineer (RHCE). These credentials are highly valued by employers and demonstrate a high level of expertise in managing RHEL environments.



### Ubuntu

#### What is Ubuntu Linux

Ubuntu is one of the most popular and widely-used Linux distributions, making it an excellent entry point for anyone looking to get started with Ubuntu. Developed by Canonical, it is built on the robust foundation of Debian and is known for its user-friendly design and strong community support. So, to answer the common question, is Ubuntu Linux? Yes, it is a polished and accessible version of the Linux operating system.

#### Package Management

As a Debian-based operating system, Ubuntu utilizes the core Debian package management system. This means it uses the apt (Advanced Package Tool) command-line utility to handle software installation, updates, and removal, giving users access to a vast repository of free and open-source software.

#### Desktop Environment

While Ubuntu historically developed its own desktop environment, Unity, the default desktop environment for modern versions is GNOME. GNOME is known for its clean, modern interface and intuitive workflow, which helps bridge the gap for users transitioning from other operating systems like Windows or macOS.

#### Why Choose Ubuntu

Ubuntu is a fantastic choice for beginners. It offers a smooth out-of-the-box experience with a great user interface, which has led to its widespread adoption. Its versatility makes it suitable for any platform, including desktops, laptops, and servers. Whether you're a developer, a student, or just a curious user, Ubuntu provides a stable and powerful environment. For hands-on practice, you can use a platform like [LabEx Ubuntu Playground](https://labex.io/tutorials/linux-online-linux-terminal-and-playground-372915) to test your skills in a real world environment.



### Fedora

#### What is Fedora

Sponsored by Red Hat, the **Fedora** project is a community-driven initiative that develops and maintains a free and open-source operating system. It is known for integrating cutting-edge technologies and providing a modern, user-friendly experience. Think of Fedora as an equivalent to Ubuntu, but built upon a Red Hat foundation instead of Debian.

#### The Relationship with Red Hat Enterprise Linux

A crucial aspect of Fedora is its role as the upstream source for **Red Hat Enterprise Linux** (RHEL). This means new features, updates, and innovations are developed and tested within the Fedora community first. After a thorough process of testing and quality assurance, these stable features are incorporated into future versions of RHEL. For developers and system administrators looking for **fedora and redhat enterprise linux answers** regarding upcoming changes, Fedora offers a preview of the future.

#### Package Management

Fedora utilizes the RPM package format and manages software with the DNF (Dandified YUM) package manager. DNF is a powerful and easy-to-use command-line tool for installing, updating, and removing software packages on the system.

#### Who Should Use Fedora

Fedora is an excellent choice for users who want a Red Hat-based operating system without the enterprise cost. It is highly recommended for desktop and laptop users, developers, and technology enthusiasts who enjoy working with the latest software. Its user-friendly nature makes it a great starting point for anyone new to the Red Hat ecosystem.



### openSUSE

#### An openSUSE Overview

The openSUSE project is a global community effort dedicated to promoting the widespread use of Linux. As one of the oldest and most established Linux distributions, openSUSE offers a remarkably stable and polished operating system. It is available in two main editions: Tumbleweed, a rolling-release for users who want the latest software, and Leap, a stable point-release that shares a common core with SUSE Linux Enterprise, ensuring enterprise-grade quality for all users.

#### Package Management with RPM

The openSUSE distro uses the RPM package manager for installing, updating, and removing software. RPM is a powerful and mature system utilized by several major Linux distros, providing access to a vast repository of software packages. This makes managing applications on your system both straightforward and efficient.

#### YaST The All-in-One Tool

A standout feature of openSUSE is YaST (Yet another Setup Tool). If you're wondering, "what is the name of openSUSE's adminstration/installation tool?", the answer is YaST. This comprehensive graphical tool simplifies nearly every aspect of system administration, from software installation to repository management to network configuration and hardware setup. The power of YaST makes openSUSE an excellent choice for anyone seeking an easy-to-manage system.

#### Getting Started with openSUSE

With its user-friendly installer and the integrated YaST control center, openSUSE is a fantastic Linux distribution for beginners. Once you donwload Linux openSuse and run the installer, you'll find a complete desktop environment ready for daily tasks, creative projects, and software development. Its stability and ease of use make it a great starting point for any user's journey into the Linux world.


## Vim Editor Notes

##### Navigation
- `h` - left
- `j` - down
- `k` - up
- `l` - right

- `CTRL-g` To see your current location in the file
- `G` (uppercase) To move to bottom of the file
- `gg` To move to start of the file
- `[line number]G` (uppercase) To navigate to a specific line

##### Commands

- `dw` To delete from the cursor up to the next word
- `de` To delete from the cursor up to the end of the word
- `d$` To delete from the cursor to the end of the line
- `dd` To delete a whole line

- `2w` To repeat a motion prepend it with a number
- `operator [number] motion` is the format for a change command
	- `operator` is what to do, such as `d` for delete
	- `[number]` is an optional count to repeat the motion
	- `motion` moves over the text to operate on, such as `w` (word), `e` (end of word), `$` (end of line), etc.
- `0` To move to start of line
- `u` (lowercase) to undo previous action
- `U` (uppercase) to undo all changes on a line
- `CTRL-R` To unto the undo's
- `p` To 'put' most previously deleted text after the cursor
- `rx` To replace the character at the cursor with x
- `ce` To change until the end of a word

- `%` To find a matching ), ], or }.

- `:s/old/new/g` To substitute 'new' for 'old', with the '`g`' flag executing this command through the line (without `g` it would only substitute the first)
- `:#,#s/old/new/g` To substitute every occurrence of a string of characters between two lines
- `:%s/old/new/g` To substitute every occurrence of a string of characters throughout the whole file
- `:%s/old/new/gc` To do the above command, with a prompt whether to substitute or not

- `:!` Allows you to execute external shell commands from the vim console. For example:
	- `:!pwd`
	- `:!ls`
	- `:!rm`
- `v` To enter 'Visual selection', which allows you to highlight text from the starting position of the cursor to wherever you move the cursor to

