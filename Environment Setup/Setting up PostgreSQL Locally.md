# How To Download and Install PostgreSQL on Your PC (Step by Step Guide For Windows Users)

### A. Download the official Windows installer
- Open the [official PostgreSQL Windows download page.](https://www.postgresql.org/download/)
Choose the latest stable version and click the Windows x86-64 installer. This is the interactive installer provided by EDB.
- Save the .exe file (e.g., postgresql-17.x-windows-x64.exe) to your Downloads folder.
Why this installer? 
It’s the easiest path for beginners and bundles PostgreSQL Server and pgAdmin 4 (GUI).

### B. Run the installer

1) Double-click the downloaded .exe. Approve the User Account Control prompt.
2) Installation Directory: keep the default (e.g., C:\Program Files\PostgreSQL\17\) unless you have a reason to change it.
3) Components: leave the defaults checked:
- PostgreSQL Server
- pgAdmin 4 (GUI)
4) Data Directory: accept the default or choose another drive/folder if you prefer.
5) Password: set a strong password for the default superuser postgres. (Write it down—you’ll need it.)
6) Port: keep 5432 (default). If you already have something on 5432, pick another (e.g., 5433).
7) Locale: keep default unless you have specific needs.
8) Click Next to install. At the end, you’ll see an option “Launch Stack Builder at exit.” You can uncheck it for now; it’s optional and used later for extras like ODBC drivers or PostGIS.

### C. Verify using pgAdmin (point-and-click)
1) Press Start and search for pgAdmin 4 (it’s installed by the same installer). 
2) Open pgAdmin → it may ask you to set a pgAdmin master password (this just protects saved connections).
3) In the left “Browser” pane, expand Servers → PostgreSQL…
4) If it’s locked, right-click → Connect and enter the postgres password you set during install.
5) If you can see Databases (1) with postgres, you’re in! Kudos :)

### D (Recommended but will be shown during virtual meeting) Enable psql from any terminal (add to PATH)
psql is the official command-line tool. Adding PostgreSQL’s bin folder to your PATH lets you run psql from any Command Prompt/PowerShell.

1) Press Start and type environment variables → open “Edit the system environment variables.”
2) Click Environment Variables… → under System variables, select Path → Edit.
3) Click New and add your PostgreSQL bin path, e.g.: *C:\Program Files\PostgreSQL\17\bin*
4) Click OK on all dialogs, then open a new Command Prompt/PowerShell window.
(Opening a new terminal is important so it picks up the updated PATH.)

### E Verify using psql (command line)
1) Open Command Prompt (Win+R → cmd) or Windows Terminal.
2) Run:
```shell
psql --version
```
You will be notified about your Postgresql version that you downloaded
3) Connect to your local server:
```shell
psql -U postgres -h localhost
```
