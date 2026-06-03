# Purpose

Teach how to use the command line (text-based interface) on macOS/Linux (Unix) and Windows.

## How to Open the Terminal / Command Prompt

Before you can run commands, you need to open your operating system's command line application:

### macOS (Terminal)
* **Spotlight Search**: Press `Cmd + Space`, type `Terminal`, and press `Enter`.
* **Applications Folder**: Open Finder, go to `Applications` -> `Utilities`, and double-click **Terminal**.

### Windows (Command Prompt)
* **Start Menu**: Press the `Windows key`, type `cmd` (or `Command Prompt`), and press `Enter`.
* **Run Dialog**: Press `Win + R`, type `cmd`, and press `Enter`.

### Linux (Terminal)
* **Keyboard Shortcut**: Press `Ctrl + Alt + T` (works on Ubuntu and most other distributions).
* **Application Launcher**: Search for `Terminal` or `Console` in your desktop environment's application menu.


## Common Command Line Operations (Quick Reference)

Below are quick reference tables comparing common commands for macOS/Linux (Bash/Zsh) and Windows (Command Prompt), organized by category.

### Navigation (Moving Around)

| Action | macOS / Linux (Bash/Zsh) | Windows (Command Prompt) |
| :--- | :--- | :--- |
| **List files in a directory** | `ls` (or `ls -la`) | `dir` |
| **Move to a folder** | `cd folder_name` | `cd folder_name` |
| **Move to parent folder** | `cd ..` | `cd ..` |

### Managing Folders (Directories)

| Action | macOS / Linux (Bash/Zsh) | Windows (Command Prompt) |
| :--- | :--- | :--- |
| **Create a folder** | `mkdir folder_name` | `mkdir folder_name` |
| **Create a sub-folder** | `mkdir -p parent/subfolder` | `mkdir parent\subfolder` |
| **Delete a folder** | `rm -rf folder_name` | `rmdir /s folder_name` |

### Managing Files

| Action | macOS / Linux (Bash/Zsh) | Windows (Command Prompt) |
| :--- | :--- | :--- |
| **Create a text file** | `touch file.txt` | `type nul > file.txt` |
| **Rename a folder/file** | `mv old_name new_name` | `ren old_name new_name` |
| **Delete a text file** | `rm file.txt` | `del file.txt` |

### Visualizing the Directory Structure

| Action | macOS / Linux (Bash/Zsh) | Windows (Command Prompt) |
| :--- | :--- | :--- |
| **Display a tree structure** | `tree` | `tree /F` |

---

## Detailed Examples & Explanations

### 1. Navigation (Moving Around)
* **List files and folders**:
  To see the list of contents in the current directory:
  * **macOS/Linux**:
    ```bash
    ls
    ```
    *(Note: Use `ls -la` to list all files, including hidden files and detailed info).*
  * **Windows (Cmd)**:
    ```cmd
    dir
    ```
  * **Interpreting the Output (Identifying Files vs. Folders)**:
    * **macOS/Linux (`ls -l` / `ls -la`)**:
      Look at the first character of the detailed output line:
      * `d` (e.g., `drwxr-xr-x`) indicates a **folder (directory)**.
      * `-` (e.g., `-rw-r--r--`) indicates a **file**.
      * `l` (e.g., `lrwxrwxrwx`) indicates a **symbolic link** (shortcut).
      *(Note: In many terminals, directories are also color-coded, e.g., in **blue**, while files are plain **white/black**).*

      **Example Output**:
      ```text
      drwxr-xr-x  2 user  group   4096 Jun  3 15:00 documentation
      -rw-r--r--  1 user  group   5522 Jun  3 15:05 todo.txt
      lrwxrwxrwx  1 user  group     12 Jun  3 15:06 shortcut -> original.txt
      ```
      *(Here, `documentation` is a folder, `todo.txt` is a file, and `shortcut` is a symbolic link).*

    * **Windows (`dir`)**:
      Look at the column preceding the name:
      * `<DIR>` indicates a **folder (directory)**.
      * A number (representing size in bytes, e.g., `5522`) indicates a **file**.

      **Example Output**:
      ```cmd
      06/03/2026  03:00 PM    <DIR>          documentation
      06/03/2026  03:05 PM             5,522 todo.txt
      ```
      *(Here, `documentation` is a folder, and `todo.txt` is a file with a size of 5,522 bytes).*


* **Move into a folder**: 
  To enter a specific folder (directory):
  ```bash
  cd folder_name
  ```
* **Move to the parent folder**:
  To go up one level to the folder that contains your current folder:
  ```bash
  cd ..
  ```


### 2. Managing Folders (Directories)
* **Create a folder**:
  ```bash
  mkdir new_folder
  ```
* **Create a sub-folder**:
  To create a folder nested inside another one (e.g., `parent_folder/child_folder`):
  * **macOS/Linux**: Use the `-p` flag to create intermediate folders if they don't exist:
    ```bash
    mkdir -p parent/child
    ```
  * **Windows**:
    ```cmd
    mkdir parent\child
    ```
* **Rename a folder**:
  * **macOS/Linux**: Use `mv` (move/rename):
    ```bash
    mv old_folder_name new_folder_name
    ```
  * **Windows (Cmd)**: Use `ren` (rename):
    ```cmd
    ren old_folder_name new_folder_name
    ```

### 3. Managing Files
* **Create an empty text file**:
  * **macOS/Linux**:
    ```bash
    touch notes.txt
    ```
  * **Windows (Cmd)**:
    ```cmd
    type nul > notes.txt
    ```

* **Delete a file**:
  * **macOS/Linux**:
    ```bash
    rm notes.txt
    ```
  * **Windows (Cmd)**:
    ```cmd
    del notes.txt
    ```

### 4. Visualizing the Directory Structure
* **Display a tree structure**:
  To see a visual tree diagram of folders and files:
  * **macOS/Linux**:
    ```bash
    tree
    ```
    *(Note: If the `tree` command is not installed, you can install it via Homebrew with `brew install tree`, or use `find .` as a built-in alternative).*
  * **Windows (Cmd)**:
    ```cmd
    tree /F
    ```
    *(Note: The `/F` flag is required on Windows to show both folders and files; without it, only folders are listed).*


---

## Student Evaluation: Real-World Scenario (Research Project Setup)

To evaluate if a student has successfully learned these commands, ask them to set up a clean, structured workspace for a scientific research project by performing the following step-by-step workflow:

### Scenario: Setting up a Research Project Workspace
The student needs to organize a new research project containing documentation (`doc`), source code (`src`), data outputs (`output`), papers (`paper`), and bibliography references (`references`).

### Step-by-Step Practical Assessment

1. **Open the Terminal / Command Prompt**:
   * Open the appropriate command-line application on your operating system (refer to the **How to Open the Terminal / Command Prompt** section above).

2. **Execute Workspace Setup Commands**:
   Type and execute the following commands in order:
   * **Initialize the Project**:
     * Create a root directory named `climate_research`.
     * Move into the `climate_research` folder.
   * **Create the Project Structure**:
     * Create a subfolder named `src`.
     * Create a subfolder named `output`.
     * Create a nested subfolder structure `paper/drafts`.
     * Create a subfolder named `references`.
     * Create a subfolder named `doc`.
   * **Initialize Documentation & Bibliography**:
     * Inside the `doc` folder, create a text file named `todo.txt`.
     * Inside the `references` folder, create a text file named `sources.txt`.
   * **Refactor and Rename**:
     * Rename the `doc` folder to `documentation`.
     * Rename the file `references/sources.txt` to `references/citations.txt`.
   * **Navigation and Cleanup**:
     * Navigate back up to the `climate_research` root folder.
     * Delete the `output` folder.
     * Navigate back out of `climate_research` to its parent folder.

3. **Capture and Filter (Grep) Command History**:
   * To verify you typed each command, filter your command history using `grep` (on macOS/Linux) or `findstr` (on Windows) and redirect the output to a text file named `submission.txt`:
     * **macOS / Linux**:
       ```bash
       history | grep -E "mkdir|cd|touch|mv|rm|ls|tree" > submission.txt
       ```
     * **Windows (Command Prompt)**:
       ```cmd
       doskey /history | findstr /R "mkdir cd type ren del dir tree" > submission.txt
       ```

4. **Verify the Final Structure**:
   * Display the directory layout using `tree` (macOS/Linux) or `tree /F` (Windows) to verify everything is set up correctly.

---

### Deliverables
* **Filtered Command History (`submission.txt`)**: The text file containing your filtered command history verifying each executed command.
* **Directory Structure Screenshot**: Take a screenshot showing the final directory structure (e.g., by running the `tree` command or showing the expanded file explorer/finder window).
* **Submission**: Submit both the `submission.txt` file and the screenshot to **iLearn** for grading.

### Evaluation Criteria
* [ ] **Terminal Launch**: Student can open the terminal or command prompt correctly.
* [ ] **Navigation**: Student can move between nested directories without getting lost (`cd`, `cd ..`).
* [ ] **Pathing**: Student understands how to create nested folders (e.g., using `mkdir -p` or Windows command equivalent).
* [ ] **File Management**: Student is able to create files inside specific folders and rename directories/files correctly.
* [ ] **Safety**: Student can safely delete files and empty or non-empty directories.
* [ ] **Verification**: Student is able to filter (grep) their terminal history to generate the verification report.



