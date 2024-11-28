### Shell script
A shell script is a text file containing a series of commands written for a shell (command-line interpreter) in Unix/Linux systems. Shell scripts automate repetitive tasks by allowing you to execute multiple commands sequentially or conditionally.
---

### **Key Points about Shell Scripts**
1. **Purpose**: Automate tasks like file manipulation, program execution, system monitoring, and more.
2. **File Extension**: Typically uses `.sh` (e.g., `myscript.sh`), though it’s not mandatory.
3. **Interpreter**: The shell script is interpreted by a shell like Bash (`/bin/bash`), Zsh, or others.
4. **Execution**:
   - To run: `sh script_name.sh` or `./script_name.sh` (with executable permissions).

---

### **Structure of a Shell Script**

#### **1. Shebang Line**
The first line specifies the interpreter to be used:
```bash
#!/bin/bash
```

#### **2. Commands and Logic**
Commands are written as you would execute them in the terminal:
```bash
#!/bin/bash
echo "Hello, World!"     # Print text
date                    # Display current date and time
```

---

### **Example: A Basic Shell Script**

#### Script: `hello.sh`
```bash
#!/bin/bash
# This script prints a greeting message and the current date

echo "Welcome to Shell Scripting!"
echo "Today's date is: $(date)"
```

#### Run the Script:
Execute:
   ```bash
   sh hello.sh
   ```

---


