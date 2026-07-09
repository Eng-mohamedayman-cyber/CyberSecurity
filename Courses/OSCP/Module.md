# Command line Fun
## Bash Environment & Variables

Linux uses environment variables to store system configurations and user data.

## Managing Variables

* env : Lists all active environment variables in your current session.
* export NAME=value : Creates a new variable or changes an existing one. (Note: Do not use spaces around the = sign).
* echo $NAME : Prints the value stored inside a specific variable.
* unset NAME : Deletes a variable from the current session.

### Making Variables Permanent
Variables created in the terminal are temporary and disappear when you close it or reboot.To make them permanent:

1. Open the configuration file: nano ~/.bashrc
2. Add your variable at the bottom: export MY_VAR="value"
3. Save the file and reload the changes: source ~/.bashrc

### ⚠️ Security Warning: Avoid creating custom variables or editing the $PATH variable with the same name as critical system commands (like sudo). If done incorrectly, the system might execute a malicious or broken script instead of the real command.

---

## Bash History

The system automatically logs every command you run into a hidden file named .bash_history.

* history : Displays a list of all previously executed commands with their line numbers.
* !<NUMBER> : Re-runs a specific command from your history using its line number (e.g., !42).
* !! : Instantly re-runs the very last command you typed.
* Ctrl + R : Opens an interactive reverse-search to find past commands by typing a keyword.

---

## Chaining Commands: ; vs &&

You can run multiple commands sequentially on a single line using these operators:

* **command1 ; command2** : Runs command2 immediately after command1 finishes, **regardless** of whether the first one succeeded or failed.
* **command1 && command2** : Runs command2 only if command1 finishes successfully (returns an exit status of 0 without errors).

---


## Data Streams & Redirection

Linux handles input and output data using three standard data streams:
* STDIN (Standard Input) : Stream 0 — Data sent into a command (usually from the keyboard).
* STDOUT (Standard Output) : Stream 1 — Normal output data displayed on the screen.
* STDERR (Standard Error) : Stream 2 — Error messages displayed on the screen.

## Output Redirection (> and >>)

* command **>** file.txt : Directs the output to a new file.

 Warning: This overwrites existing file content; old data cannot be restored.
 
 * command **>>** file.txt : Appends the output to the end of a file, keeping the old content safe.
 * command **2>** error.txt : Redirects only the error messages (Stream 2) into a separate file.
 
 Example: ls -l fake_file > output.txt 2> error.txt saves the error message into error.txt.

## Input Redirection (<)

* command **<** file.txt : Feeds the content of a file directly into a command as its input.
  Example: If A="file.txt", then cat < $A will print the file contents. If A="text_string", it will cause an error because a string is not a valid file path.

---

## Piping & Advanced Tools

Piping allows you to connect commands together by sending the output of one tool directly into another.
### | (Pipe) : 
Passes the output of the left tool as the input to the right tool.

* Example: cat flag.txt | wc sends the file text into wc. The final result only displays the word count.
### wc : 
Counts and displays the number of lines, words, and characters in a file.
### tee : Splits the data stream. It saves the output into a file and displays it on the terminal screen at the same time.

* Example: cat file.txt | tee new_file.txt
### xargs : Captures the output of a command and converts it into arguments for another command.

* Example: ls | xargs rm gathers the list of all files in the directory and deletes them all at once.
