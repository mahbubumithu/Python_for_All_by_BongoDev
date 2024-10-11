**Basic Linux Commands for Day-to-Day Usage**.

---

### **Navigating Directories**

- **pwd (Print Working Directory)**  
  Displays the current directory you're in.

  ```linux
  $ pwd
  ```

  _Example output:_ `/home/user`

- **ls (List)**  
  Lists files and directories in the current directory.

  ```bash
  $ ls
  ```

  _Example output:_ `Documents/  Downloads/  Pictures/`

- **cd (Change Directory)**  
  Changes the current directory.
  ```bash
  $ cd /home/user/Documents
  ```

---
### **Common `ls` Options**

- **1. `ls -l` (Long Format)**  
  Displays detailed information about files, including permissions, owner, size, and last modified date.

  ```bash
  $ ls -l
  ```

  _Example output:_  
  `-rw-r--r-- 1 user user 4096 Oct 11 10:15 file.txt`

- **2. `ls -a` (All Files)**  
  Lists all files, including hidden files (files starting with `.`).

  ```bash
  $ ls -a
  ```

  _Example output:_  
  `.bashrc  .hiddenfile  Documents/`

- **3. `ls -h` (Human-Readable Format)**  
  Displays file sizes in human-readable format (e.g., KB, MB).

  ```bash
  $ ls -lh
  ```

  _Example output:_  
  `-rw-r--r-- 1 user user 4.0K Oct 11 10:15 file.txt`

- **4. `ls -r` (Reverse Order)**  
  Lists files and directories in reverse order.

  ```bash
  $ ls -r
  ```

  _Example output:_  
  `Videos/  Pictures/  Downloads/  Documents/`

- **5. `ls -t` (Sort by Modification Time)**  
  Sorts files by their modification time, with the most recently modified files appearing first.

  ```bash
  $ ls -lt
  ```

  _Example output:_  
  `-rw-r--r-- 1 user user 4096 Oct 11 10:15 recent.txt`

- **6. `ls -S` (Sort by Size)**  
  Sorts files by size, with the largest files displayed first.
  ```bash
  $ ls -lS
  ```

---

To copy a folder in Linux, you can use the `cp` command with the `-r` (recursive) option. Here's how it works:

---

### **Copying a Folder in Linux**

- **Basic Syntax**:

  ```bash
  cp -r <source_folder> <destination>
  ```

- **Key Option**:
  - **`-r` or `--recursive`**: This tells `cp` to copy all files and subdirectories inside the folder recursively.

---

### **Examples of Copying a Folder**

1. **Copy a folder to another location**:

   ```bash
   cp -r /home/user/Documents/project /home/user/Backup/
   ```

   _This will copy the `project` folder and all its contents to the `Backup` directory._

2. **Copy a folder and rename it**:

   ```bash
   cp -r /home/user/Documents/project /home/user/Backup/project_copy
   ```

   _This will copy the `project` folder and rename the copied version to `project_copy` in the `Backup` directory._

3. **Copy a folder to the current directory**:
   ```bash
   cp -r /home/user/Documents/project .
   ```
   _This will copy the `project` folder from `/Documents` to the current working directory._

---
### **Managing Files**

- **touch**  
  Creates an empty file or updates a file's timestamp.

  ```bash
  $ touch newfile.txt
  ```

- **cp (Copy)**  
  Copies files or directories.

  ```bash
  $ cp file1.txt /home/user/Backup/
  $ cp -r /home/user/Documents/project /home/user/Backup/
  ```

- **mv (Move/Rename)**  
  Moves or renames files or directories.

  ```bash
  $ mv oldname.txt newname.txt
  ```

- **rm (Remove)**  
  Deletes files and folders.
  ```bash
  $ rm file1.txt
  $ rm -rf folder/
  ```

---

### **Viewing File Content**

- **cat**  
  Displays the contents of a file.

  ```bash
  $ cat file.txt
  ```

- **less**  
  View file content one screen at a time.

  ```bash
  $ less largefile.txt
  ```

- **head / tail**  
  Shows the first/last 10 lines of a file.
  ```bash
  $ head file.txt
  $ tail file.txt
  ```

---

### **System Monitoring Commands**

- **top**  
  Displays a real-time view of running processes.

  ```bash
  $ top
  ```

- **df (Disk Free)**  
  Shows available disk space on file systems.

  ```bash
  $ df -h
  ```

- **free**  
  Displays available and used memory.
  ```bash
  $ free -h
  ```

---

### **Searching & Finding Files**

- **find**  
  Search for files in a directory hierarchy.

  ```bash
  $ find /home/user -name "file.txt"
  ```

- **grep**  
  Searches for a pattern within files.
  ```bash
  $ grep "error" logfile.txt
  ```

---

### **Basic Networking Commands**

- **ping**  
  Checks the connectivity to another machine.

  ```bash
  $ ping google.com
  ```

- **ifconfig / ip**  
  Displays or configures network interfaces.
  ```bash
  $ ifconfig
  $ ip addr show
  ```

---
**file permissions**

---

### **Slide: Understanding File Permissions in Linux**

- **What are File Permissions?**
  - File permissions determine who can read, write, or execute a file or directory.
  - Every file has three permission types:
    - **Read (r)**: Ability to view the contents of a file or list a directory’s contents.
    - **Write (w)**: Ability to modify or delete a file or its contents.
    - **Execute (x)**: Ability to run a file as a program or access a directory.

---

### **Slide: File Permission Structure**

- **Viewing Permissions**  
  Use `ls -l` to see permissions for files and directories:
  ```bash
  $ ls -l
  ```
  *Example output:*  
  `-rwxr-xr-- 1 user group 4096 Oct 11 10:15 script.sh`

  - **Permission Breakdown**:
    - `-rwxr-xr--`
      - The first character: `-` (file) or `d` (directory).
      - **Owner**: `rwx` (read, write, execute for the file owner).
      - **Group**: `r-x` (read, execute for users in the file's group).
      - **Others**: `r--` (read-only for all others).

---

### **Slide: Changing File Permissions with `chmod`**

- **Basic Syntax**:
  ```bash
  chmod <permissions> <file>
  ```

- **1. Using Numeric Mode**
  - Permissions can be represented by numbers:
    - `4` = Read (r)
    - `2` = Write (w)
    - `1` = Execute (x)
  - Combine these for different roles:
    - **Owner** | **Group** | **Others**: 777 (rwx for all), 644 (rw- for owner, r-- for group and others)

  **Example:**
  ```bash
  chmod 755 script.sh
  ```
  *This gives the owner full access (rwx), while group and others get read and execute access (r-x).*

- **2. Using Symbolic Mode**
  - Permissions can also be changed with symbols:
    - `u` = user/owner
    - `g` = group
    - `o` = others
    - `a` = all (user, group, others)

  **Example:**
  ```bash
  chmod u+x script.sh
  ```
  *This adds execute permission to the owner.*

  **Example:**
  ```bash
  chmod g-w file.txt
  ```
  *This removes write permission for the group.*

---

### **Slide: Common `chmod` Examples**

1. **Give execute permission to all users**:
   ```bash
   chmod a+x script.sh
   ```

2. **Remove write permission for others**:
   ```bash
   chmod o-w file.txt
   ```

3. **Set full permissions for the owner, read-only for group and others**:
   ```bash
   chmod 744 file.txt
   ```

---

### **Slide: Changing File Ownership with `chown`**

- **`chown`** allows you to change the owner and group of a file.
  ```bash
  chown <owner>:<group> <file>
  ```

- **Example: Change the owner to `user1` and group to `staff`**:
  ```bash
  chown user1:staff file.txt
  ```

- **Change ownership of a directory recursively**:
  ```bash
  chown -R user1:staff /path/to/directory
  ```

---

### **Slide: Viewing Effective Permissions with `stat`**

- Use `stat` to view detailed file permissions and other metadata:
  ```bash
  stat file.txt
  ```
  *This will show the numeric mode (e.g., 0644) and other attributes of the file.*

---

### **Slide: Understanding Special Permissions**

- **Setuid (Set User ID)**: Allows a file to be executed with the permissions of its owner.
  ```bash
  chmod u+s file.sh
  ```

- **Setgid (Set Group ID)**: Ensures new files created in a directory inherit the group of the directory.
  ```bash
  chmod g+s directory/
  ```

- **Sticky Bit**: Prevents users from deleting files in a directory unless they own them.
  ```bash
  chmod +t /shared_directory
  ```

---

This expanded section provides an in-depth understanding of file permissions, `chmod`, `chown`, and special permission settings in Linux.

---

### **Package Management (Ubuntu Example)**

- **apt-get update**  
  Updates the package lists.

  ```bash
  $ sudo apt-get update
  ```

- **apt-get install**  
  Installs a package.
  ```bash
  $ sudo apt-get install vim
  ```

---

## Explore further

1. [More on `ls` and `cp`](file/ls-and-cp.md)
2. [File Permissions](file/permissions.md)
