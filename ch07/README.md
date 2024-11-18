### Chapter 7: Scripting and the Shell - Summary with Example Codes

#### **7.1 Scripting Philosophy**
- **Microscripts**: Create small, targeted scripts to automate repetitive tasks.
- **Learn Tools Well**: Master tools like `grep`, `awk`, `sed`, and the shell.
- **Automation**: Strive to automate tasks to save time and reduce errors.
- **Choose the Right Language**:
  - Use Bash for quick scripts.
  - Choose Python or Ruby for complex tasks.
- **Best Practices**:
  - Keep scripts readable.
  - Use version control (e.g., Git).
  - Avoid premature optimization.

Example:
```bash
# A simple microscript to back up a directory
#!/bin/bash
tar -czf backup.tar.gz /path/to/directory
echo "Backup completed."
```

---

#### **7.2 Shell Basics**
- **Command Editing**: Use shortcuts like `Ctrl+A` (beginning of line), `Ctrl+E` (end of line).
- **Pipes and Redirection**:
  - Pipe output: `ls | grep file`
  - Redirect output: `command > file.txt`
- **Variables**:
  ```bash
  MY_VAR="Hello"
  echo $MY_VAR
  ```
- **Environment Variables**:
  ```bash
  export PATH=$PATH:/new/path
  ```

---

#### **7.3 `sh` Scripting**
- **Execution**:
  ```bash
  bash script.sh
  chmod +x script.sh
  ./script.sh
  ```
- **Input/Output**:
  ```bash
  read -p "Enter your name: " name
  echo "Hello, $name!"
  ```
- **Control Flow**:
  ```bash
  if [ $1 -eq 5 ]; then
    echo "Five"
  else
    echo "Not five"
  fi
  ```
- **Loops**:
  ```bash
  for file in *.txt; do
    echo $file
  done
  ```

---

#### **7.4 Regular Expressions**
- **Literal Characters**:
  ```bash
  grep "pattern" file.txt
  ```
- **Special Characters**:
  - `.`: Matches any character.
  - `*`: Matches zero or more of the preceding element.
- **Example**:
  ```bash
  grep -E "^[a-z]+@[a-z]+\.[a-z]{2,}$" emails.txt
  ```

---

#### **7.5 Python Programming**
- **Quick Start**:
  ```python
  print("Hello, World!")
  ```
- **Data Structures**:
  ```python
  my_list = [1, 2, 3]
  my_dict = {"key": "value"}
  ```
- **Example**: Input Validation
  ```python
  import re
  email = input("Enter email: ")
  if re.match(r"^[a-z]+@[a-z]+\.[a-z]{2,}$", email):
      print("Valid email")
  else:
      print("Invalid email")
  ```

---

#### **7.6 Ruby Programming**
- **Quick Start**:
  ```ruby
  puts "Hello, World!"
  ```
- **Regular Expressions**:
  ```ruby
  if "test@example.com" =~ /^[a-z]+@[a-z]+\.[a-z]{2,}$/
    puts "Valid email"
  end
  ```

---

#### **7.7 Library and Environment Management for Python and Ruby**
- **Python**:
  - Use `pip` for package management.
  ```bash
  pip install requests
  ```
  - Use `venv` for virtual environments:
  ```bash
  python -m venv env
  source env/bin/activate
  ```
- **Ruby**:
  - Use `gem` for package management.
  ```bash
  gem install bundler
  ```
  - Manage environments with tools like RVM or rbenv.

---

#### **7.8 Revision Control with Git**
- **Basics**:
  ```bash
  git init
  git add .
  git commit -m "Initial commit"
  ```
- **Branching**:
  ```bash
  git branch new_feature
  git checkout new_feature
  ```
- **Collaborative Work**:
  ```bash
  git push origin main
  git pull origin main
  ```

---

#### **7.9 Recommended Reading**
- Explore resources to deepen your understanding of:
  - Shell scripting.
  - Python and Ruby programming.
  - Advanced Git workflows.

This summary includes foundational concepts and examples to support learning scripting and automation. Let me know if you'd like further details!