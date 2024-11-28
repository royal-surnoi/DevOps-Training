### Basic Commands

---

### **1. `pwd` (Print Working Directory)**
- Shows the current directory you are in.  
- Example: If you're in `/home/user`, running `pwd` will display `/home/user`.

---

### **2. `mkdir <repo_name>` (Make Directory)**
- Creates a new directory (folder).  
- Example: `mkdir my_folder` creates a folder named "my_folder".

---

### **3. `cd` (Change Directory)**
- Lets you move into a different directory.  
- Example: `cd my_folder` moves you into the "my_folder" directory.  
- Tip: Use `cd ..` to move up one directory.

---

### **4. `ls -l` (List Files)**
- Lists all files and directories in the current directory in a detailed format (permissions, size, etc.).  
- Example: Run `ls -l` to see detailed info about files in the current folder.

---

### **5. `touch <file_name>`**
- Creates an empty file.  
- Example: `touch file.txt` creates a file named "file.txt".

---

### **6. `echo "Hello World!" > sample.txt`**
- Writes text ("Hello World!") into a file (`sample.txt`).  
- Example: After running this, `cat sample.txt` will show "Hello World!".

---

### **7. `cat <file_name>`**
- Displays the contents of a file.  
- Example: `cat sample.txt` shows what's inside "sample.txt".

---

### **8. `rm sample.txt` (Remove File)**
- Deletes a file.  
- Example: `rm sample.txt` deletes the file named "sample.txt".

---

### **9. `rmdir demo/` (Remove Directory)**
- Deletes an **empty folder**.  
- Example: `rmdir demo/` deletes the "demo" directory if it's empty.

---

### **10. `rm -rf test/`**
- Deletes a folder and all its contents (files and subfolders).  
- Example: `rm -rf test/` deletes the "test" directory and everything inside it.  
- Warning: Be careful with this command, as it **permanently** deletes data.

---

### **11. `rm --help` / `man rm`**
- Shows help or manual for the `rm` command.  
- Example: `rm --help` lists options for the `rm` command, like `-r` or `-f`.

---

### **12. `cp` (Copy)**
- Copies a file or folder to another location.  
- Example: `cp file.txt /backup/` copies "file.txt" to the "backup" folder.

---

### **13. `mv` (Move or Rename)**
- Moves files/folders or renames them.  
- Example 1: `mv file.txt /backup/` moves "file.txt" to the "backup" folder.  
- Example 2: `mv old_name.txt new_name.txt` renames "old_name.txt" to "new_name.txt".

---

### **14. `wc` (Word Count)**
- Counts the lines, words, and characters in a file.  
- Example: `wc file.txt` shows something like `3 5 20`, meaning 3 lines, 5 words, and 20 characters.

---

### **15. `history`**
- Displays a list of previously run commands.  
- Example: `history` might show:
  ```
  1  pwd
  2  ls
  3  cd my_folder
  ```

---

### **16. `head`**
- Displays the first 10 lines of a file by default.  
- Example: `head file.txt` shows the first 10 lines of "file.txt".  
- Use `head -n 5 file.txt` to see the first 5 lines.

---

### **17. `less`**
- Lets you view a file one page at a time.  
- Example: `less large_file.txt` allows you to scroll through a big file using the arrow keys.  
- Press `q` to exit `less`.

---

These commands help you manage files and directories, view content, and understand system operations efficiently.

### Vi Editor 
Here’s a simple explanation of the **`vi`** editor commands and similar ones:

---

### **1. `vi <file_name>`**
- Opens a file in the `vi` text editor.  
  - If the file exists, it will open the file for editing.  
  - If the file doesn’t exist, it creates a new one.

---

### **2. `i` (Insert Mode)**
- Press `i` to start inserting or editing text in the file.  
- Without pressing `i`, you cannot type or modify anything.

---

### **3. `:wq!` (Save and Exit)**
- Saves the changes made to the file and exits `vi`.  
- `:wq!` ensures the file is saved even if it is read-only.

---

### **4. `:q!` (Quit Without Saving)**
- Exits the `vi` editor **without saving any changes**.  
- Use this if you accidentally made unwanted changes.

---

### Similar Commands in `vi`:
| **Command**       | **Explanation**                                                    |
|--------------------|--------------------------------------------------------------------|
| `:w`              | Saves the file **without exiting**.                                |
| `:x`              | Saves the file and exits (same as `:wq`).                          |
| `/search_term`     | Searches for a word or term in the file.                          |
| `n`               | Moves to the **next match** when searching.                       |
| `u`               | **Undo** the last change.                                         |
| `dd`              | Deletes the current line.                                         |
| `yy`              | Copies (yanks) the current line.                                  |
| `p`               | Pastes the copied or deleted line below the current line.         |
| `:set number`     | Displays line numbers in the file.                                |
| `:set nonumber`   | Hides line numbers.                                               |

---

### Example Workflow:
1. Open a file: `vi myfile.txt`
2. Enter insert mode: Press `i`
3. Write text: *Type your content*
4. Save and exit: Press `Esc` and type `:wq`  
   - If you want to quit without saving, type `:q!`.



### User management 

sudo adduser <username>
sudo passwd 
sudo deluser <username>
sudo deluser --remove-home <username>
cat /etc/passwd
id 
whoami 

### group management
sudo groupadd developers
groups <username>
sudo usermod -aG groupname username
sudo gpasswd --delete <username> <group>
sudo gpasswd --d <username> <group>

### Permissions

### SSH authentication