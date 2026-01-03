# 📘 Git Day-1 — Install git and Create Bare Repository 

🎯 Task Objective
Set up Git on the Storage Server and create a bare Git repository for the Nautilus development team.
🖥️ Server (Stratos DC)
Server Name: Storage Server
Host: ststor01
User: root

# 🔹 Step 1: Check if Git is installed (optional check)
git --version

🔹 Purpose:
Checks whether Git is already installed and confirms the installed version.

# 🔹 Step 2: Install Git using yum
sudo yum install -y git

🔹 Explanation:
yum → Package manager for RHEL/CentOS
install → Installs a package
-y → Automatically answers “yes” to prompts
git → Package name
✅ Result: Git is installed on the Storage Server.

# 🔹 Step 3: Verify Git installation
git --version

🔹 Confirms Git was installed successfully and is available system-wide.

# 🔹 Step 4: Create a bare Git repository
sudo git init --bare /opt/demo.git

🔹 Explanation:
git init → Initializes a Git repository
--bare → Creates a bare repository
No working directory
Used as a central/shared repository
/opt/demo.git → Repository path (exact name required)
✅ Result: Bare repository created for team collaboration.

# 🔹 Step 5: Verify repository directory
ls -ld /opt/demo.git

🔹 Shows:
Directory permissions
Owner and group
Confirms the repo exists

# 🔹 Step 6: Verify bare repository structure
ls /opt/demo.git

🔹 Expected output:
HEAD
branches
config
hooks
objects
refs

# 🔹 Meaning:
These files confirm it is a bare Git repository
No project files or working tree (as expected)

# ✅ Final Outcome
✔ Git installed via yum
✔ Bare repository created at /opt/demo.git
✔ Repository verified and ready for developer use

# 🧠 Key Concept (Interview Tip)
Bare repository = Central repo used for:
git clone
git push
git pull
Developers do not edit files directly inside a bare repo.