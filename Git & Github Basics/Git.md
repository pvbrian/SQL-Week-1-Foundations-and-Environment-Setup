# Introduction To Git

## 1. What is Git?
- Git is a version control system that tracks changes in your code or project files especially on GitHub.
- Expect demo during virtual meeting.

## 2. How to Install Git Bash (For Windows Users)
- Because our end goal is to set up Gitbash into VS Code as it's editor, let's first Install VS Code

### A. How To Install Visual Studio Code aka. VS Code (For Windows Users)
1) To Download: click this (link)[https://code.visualstudio.com/download]
2) Click the big "Windows" button to download the installer.
3) Run the Installer: Double-click the downloaded .exe file.
4) Follow the Setup Wizard: Again, defaults are mostly fine, but I recommend these changes:
- Select Additional Tasks: Check "Add to PATH" and "Register Code as an editor for supported file types". The "Add to PATH" option is crucial for the next step.
5) Complete the installation.


### B. How To Install Git Bash

1) Download: Go to the (official Git website)[https://git-scm.com/download/win.] The download for the standalone 64-bit Git for Windows Setup should start automatically.
2) Run the Installer: Double-click the downloaded .exe file.
3) Follow the Setup Wizard: You can mostly just click "Next" with the default options, with these key exceptions:
- Select Components: Check "Windows Explorer integration" > "Git Bash Here". This lets you right-click in any folder and open Git Bash there.
- Choosing the default editor: The default is Vim, which is confusing for beginners. Scroll down and select "Use Visual Studio Code as Git's default editor". (We'll install VS Code next).
- Adjusting your PATH environment: Choose "Git from the command line and also from 3rd-party software". This is the safest and most useful option.
- Choose HTTPS transport backend: Use the default "Use the OpenSSL library".
- Configuring the line ending conversions: This is critical! Select "Checkout Windows-style, commit Unix-style line endings". This ensures your code works well on both Windows and Linux/macOS systems.
- Choose the terminal emulator: Choose "Use MinTTY (the default terminal of Git Bash)".
- Extra Options: Leave the defaults.
4) Complete the installation.
- Verify it works: Press the Windows key, type Git Bash, and open it. A terminal window should open. Type git --version and press Enter. You should see a version number. You're good to go! Kudos : )


### C. Setup Git Bash in VS Code Terminal
This lets you use the powerful Git Bash terminal inside your VS Code editor.

1) Open VS Code.
2) Open the integrated terminal: Press Ctrl + ` (backtick, usually next to the '1' key).
3) By default, it might open PowerShell. Click the dropdown arrow (v) in the terminal panel and select "Select Default Profile".
4) A list of available terminals appears. Choose Git Bash.
5) Now, click the dropdown again and click "New Terminal" (or press Ctrl + Shift + `). Your new terminal should now be a Git Bash terminal! You can run git commands here directly.

## Core Git Concepts:

Here are the **must-know Git concepts** with their meaning and when to use them.

| Concept       | Meaning | When to Use |
|---------------|---------|-------------|
| **Repository (repo)** | A project folder tracked by Git. | Start tracking changes for a project. |
| **Clone**     | Make a copy of a repo from GitHub to your computer. | Start working on an existing project. |
| **Commit**    | A saved snapshot of your project changes. | Whenever you finish a logical piece of work (e.g., fixed a bug). |
| **Branch**    | A separate line of development. | To add new features or test ideas without breaking the main code. |
| **Merge**     | Combine changes from one branch into another. | To bring a finished feature back into the main branch. |
| **Push**      | Upload commits from your computer to GitHub. | To share your work online. |
| **Pull**      | Download changes from GitHub to your computer. | To update your local project with the latest team changes. |
| **Pull Request (PR)** | A request to merge your branch into another on GitHub. | To get your changes reviewed and added. |
| **Staging Area** | A place where changes wait before being committed. | To prepare only specific changes for commit. |
| **.gitignore** | A file listing things Git should ignore. | To avoid committing files like secrets or temporary files. |

---

## Git Workflow (Demo will be shown in Virtual Meeting)
Your First Git Workflow Will Look Like This:

1) git clone <project-url> (get the project from GitHub)
2) git checkout -b my-new-feature (create a new branch for your work)
3) (Make your changes to files in VS Code)
4) git add . (stage all changed files)
5) git commit -m "Describe what you did" (create a local save point)
6) git push origin my-new-feature (upload your branch and changes to GitHub)