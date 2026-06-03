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
| **Move to a folder** | `cd folder_name` | `cd folder_name` |
| **Move to parent folder** | `cd ..` | `cd ..` |
| **List files in a directory** | `ls` (or `ls -la`) | `dir` |

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

To evaluate if a student has successfully learned these commands, ask them to set up a clean, structured workspace for a scientific research project.

### Scenario: Setting up a Research Project Workspace
The student needs to organize a new research project containing documentation (`doc`), source code (`src`), data outputs (`output`), papers (`paper`), and bibliography references (`references`).

### Practical Assessment Checklist

1. **Initialize the Project Directory**:
   * Create a root directory named `climate_research`.
   * Move into the `climate_research` folder.

2. **Create the Project Structure**:
   * Create a subfolder named `src` (for source code).
   * Create a subfolder named `output` (for data results and plots).
   * Create a nested subfolder structure `paper/drafts` (for writing the paper).
   * Create a subfolder named `references` (for PDF articles and bib files).
   * Create a subfolder named `doc` (for general project notes).

3. **Initialize Documentation & Bibliography**:
   * Inside the `doc` folder, create a text file named `todo.txt` (to list project tasks).
   * Inside the `references` folder, create a text file named `sources.txt` (to track bibliography).

4. **Refactor and Rename**:
   * Rename the `doc` folder to `documentation` to make it more descriptive.
   * Rename the file `references/sources.txt` to `references/citations.txt`.

5. **Navigation and Cleanup**:
   * Navigate back up to the `climate_research` root folder.
   * Assume the `output` folder was generated by mistake, and delete the `output` folder.
   * Navigate back out of `climate_research` to its parent folder.

---

### Evaluation Criteria
* [ ] **Navigation**: Student can move between nested directories without getting lost (`cd`, `cd ..`).
* [ ] **Pathing**: Student understands how to create nested folders (e.g., using `mkdir -p` or Windows command equivalent).
* [ ] **File Management**: Student is able to create files inside specific folders and rename directories/files correctly.
* [ ] **Safety**: Student can safely delete files and empty or non-empty directories.

### Deliverables
* **Directory Structure Screenshot**: Take a screenshot showing the final directory structure (e.g., by running the `tree` command or showing the expanded file explorer/finder window).
* **Submission**: Submit the screenshot to **iLearn** for grading.



