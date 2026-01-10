# Git-Day-4 : Update Git Repository with Sample HTML File
# Q.
Update Git Repository with Sample HTML File-Day-4-git The Nautilus development team has initiated a new project development, establishing various Git repositories to manage each project's source code. Recently, a repository named /opt/ecommerce.git was created. The team has provided a sample index.html file located on the jump host under the /tmp directory. This repository has been cloned to /usr/src/kodekloudrepos on the storage server in the Stratos DC.
Copy the sample index.html file from the jump host to the storage server placing it within the cloned repository at /usr/src/kodekloudrepos/ecommerce.
Add and commit the file to the repository.
Push the changes to the master branch.
--------------------------------------------------------------------------------------------------

# 🖥️ Step 1: Copy index.html from Jump Host to Storage Server
From storage server, run:
scp jump_host:/tmp/index.html /usr/src/kodekloudrepos/ecommerce/

👉 If the jump host requires a user:

scp user@jump_host:/tmp/index.html /usr/src/kodekloudrepos/ecommerce/
✔️ This copies index.html into the cloned repository.

# 📁 Step 2: Go to the Repository Directory
cd /usr/src/kodekloudrepos/ecommerce

Verify file:
ls

You should see:
index.html

# ➕ Step 3: Add the File to Git
git add index.html

Check status:
git status

# 📝 Step 4: Commit the File
git commit -m "Add sample index.html file"

🚀 Step 5: Push to Master Branch
git push origin master

# ✅ Final Verification (Optional)
git log --oneline

You should see your commit message.
🎉 Task Completed!
Your index.html is now:
================================================================================================

# 📄 Day-4 Git Task – One-Page Command Sheet
🎯 Goal
Copy index.html from jump host → storage server,
add it to the Git repo, commit, and push to master.

# 🖥️ STEP 1: Copy file from Jump Host to Storage Server
sudo scp /tmp/index.html natasha@ststor01:/home/natasha/

Explanation (one-line):
Copies index.html from jump host /tmp to natasha’s home directory (writable location).
📌 Why?
scp cannot use sudo on the remote system, and /usr/src is root-owned.

# 🔐 STEP 2: Login to Storage Server
ssh natasha@ststor01

Explanation:
Logs in as user natasha on the storage server.

# 📁 STEP 3: Move file into Git repository (as root)
sudo mv /home/natasha/index.html /usr/src/kodekloudrepos/ecommerce/

Explanation:
Moves the file into the cloned Git repo using root permissions.

# 🔑 STEP 4: Switch to Root User
sudo su -

Explanation:
Becomes root so Git can write to .git/ directory.
📌 Important:
The repository is owned by root, not natasha.

# 📂 STEP 5: Go to the Repository
cd /usr/src/kodekloudrepos/ecommerce

Explanation:
Enters the cloned Git repository directory.

# ➕ STEP 6: Add the File to Git
git add index.html

Explanation:
Stages index.html for commit.

# 📝 STEP 7: Commit the File
git commit -m "Add sample index.html file"

Explanation:
Creates a commit with a clear message.

# 🚀 STEP 8: Push to Master Branch
git push origin master

Explanation:
Pushes the commit to the remote repository’s master branch.

# ✅ STEP 9: Verify (Optional)
git log --oneline

Explanation:
Confirms the commit was created successfully.
===============================================================================================

# 📄 Day-4 Git Task

# 🖥️ On Jump Host (thor)
sudo scp /tmp/index.html natasha@ststor01:/home/natasha/   # Securely copy index.html to natasha's home (writable location)

# 🔐 Login to Storage Server
ssh natasha@ststor01                                       # Connect to storage server as natasha

# 📁 Move File into Git Repository
sudo mv /home/natasha/index.html /usr/src/kodekloudrepos/ecommerce/   # Move file into root-owned Git repo using sudo

# 🔑 Switch to Root User (Required for Git)
sudo su -                                                   # Become root to get write access to .git directory

# 📂 Navigate to Repository
cd /usr/src/kodekloudrepos/ecommerce                        # Enter the cloned ecommerce Git repository

# ➕ Stage the File
git add index.html                                         # Add index.html to Git staging area

# 📝 Commit the File
git commit -m "Add sample index.html file"                 # Create a commit with a meaningful 
message

# 🚀 Push to Master Branch
git push origin master                                     # Push commit to remote master branch

# ✅ Verify (Optional but Safe)
git log --oneline                                          # Verify commit exists in Git history

⚠️ Exam Warnings (Must Remember)
scp cannot use sudo on remote side
/usr/src is root-owned
safe.directory ≠ permission fix
Git must run as repo owner (root)

# 🧠 Golden Exam Rule
Permission denied in scp  → copy to home → sudo mv
Permission denied in git  → sudo su -
✅ Final State
✔️ index.html copied
✔️ Added to Git
✔️ Committed
✔️ Pushed to master