# Text Searching and Manipulation

Processing and filtering raw text data is a critical skill in penetration testing for parsing tool outputs, log files, and wordlists.

---

## 1. grep (Global Regular Expression Print)

Used to search for specific text patterns or Regular Expressions (Regex) inside files.

**Syntax:** `grep [options] <search-text> <file_name>`

### Key Options:
* `-i` : Ignore case (matches both uppercase and lowercase letters).
* `-v` : Invert match (displays only the lines that do **not** match the pattern).

### Advanced Usage & Examples:
* **Search for multiple patterns simultaneously:**
  ```bash
  grep "pwd\|password\|pass" 10k-most-common.txt
  ```
* **Match any line containing a numeric digit (0-9):**
  ```bash
  grep "[0-9]" 10k-most-common.txt
  ```
* **Match lines starting with a specific pattern (`^` anchor):**
  ```bash
  grep "^pwd" 10k-most-common.txt
  ```
* **Match an exact word length using wildcards (`.` represents any single character):**
  ```bash
  grep "^p.....s\$" 10k-most-common.txt
  ```
* **Match lines starting with a specific character range (a to f):**
  ```bash
  grep "^[a-f]" 10k-most-common.txt
  ```

---

## 2. sed (Stream Editor)

Used to transform, find, and replace text patterns within a data stream dynamically.

**Syntax:** `sed 's/<target_text>/<replacement_text>/options' <file_name>`

### Examples:
* **Replace the first occurrence per line (Terminal view only):**
  ```bash
  sed 's/password/admin/' S.txt
  ```
  *Note: To save changes permanently, redirect the output: `sed 's/password/admin/' S.txt > new.txt`*
* **Global replacement (`g` flag replaces all occurrences on every line):**
  ```bash
  sed 's/password/admin/g' S.txt
  ```

---

## 3. split

Used to break large text files (like giant wordlists) into smaller, manageable chunks based on line count.

**Syntax:** `split -l <number_of_lines> <file_to_split> <prefix_name>`

### Examples:
* **Split a file into files of 100 lines each:**
  ```bash
  split -l 100 S.txt split_file_
  ```
* **Split the giant RockYou wordlist into chunks of 1,000,000 lines:**
  ```bash
  split -l 1000000 rockyou.txt pass_
  ```

---

## 4. head & tail

Used to view the top or bottom boundaries of a text file without loading the entire document into memory.

**Syntax:** 
* `head -n <number_of_lines> <file_name>`
* `tail -n <number_of_lines> <file_name>`

### Examples:
* **View the first 20 lines of a wordlist:**
  ```bash
  head -n 20 10k-most-common.txt
  ```
* **View the last 15 lines of a log file:**
  ```bash
  tail -n 15 /var/log/syslog
  ```

---

## 5. cut & awk

Used for advanced column extraction and data parsing.

### cut Command
Best for simple delimiters (like colons, commas, or dashes).

**Syntax:** `cut -d '<delimiter>' -f <field_numbers> <file_name>`

* **Extract the first field (e.g., usernames) from a colon-separated file:**
  ```bash
  cut -d ":" -f 1 emails.txt
  ```

### awk Utility
A powerful programming language designed for advanced pattern scanning and processing (handles irregular whitespace spaces automatically).

**Syntax:** `awk '[condition] {print $<column_number>}' <file_name>`

* **Extract the first column from a file:**
  ```bash
  awk '{print \$1}' emails.txt
  ```
* **Print specific columns separated by a space:**
  ```bash
  awk '{print \$1, \$2}' emails.txt
  ```
* **Print the entire line if it contains the word "password" (Pattern matching):**
  ```bash
  awk '/password/{print}' emails.txt
  ```
* **Conditional filtering using logical operators:**
  ```bash
  awk '{if (\$1 ~ /password/) print}' 10k-most-common.txt
  ```

---

## 6. Comparing Files (comm & diff)

Used to analyze and find variations or commonalities between two files.

### comm Command
Compares two **sorted** files line by line and outputs three columns: (1) Unique to File1, (2) Unique to File2, (3) Common to both.

**Syntax:** `comm [options] <file1> <file2>`

* `-1` : Suppress column 1 (lines unique to file1).
* `-2` : Suppress column 2 (lines unique to file2).
* `-3` : Suppress column 3 (lines common to both files).

* **Display ONLY lines that are common to both File1 and File2:**
  ```bash
  comm -12 F1.txt F2.txt
  ```

### diff Command
Displays the exact structural differences and edits needed to make two files identical.

**Syntax:** `diff <file1> <file2>`
