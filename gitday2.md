# Day-2 : Clone Git Repository on Storage Server
# Q.
The DevOps team established a new Git repository last week, which remains unused at present. However, the Nautilus application development team now requires a copy of this repository on the Storage Server in the Stratos DC. Follow the provided details to clone the repository:

The repository to be cloned is located at /opt/official.git

Clone this Git repository to the /usr/src/kodekloudrepos directory. Perform this task using the natasha user, and ensure that no modifications are made to the repository or existing directories, such as changing permissions or making unauthorized alterations.
--------------------------------------------------------------------------------------------------

# 1️⃣ Login to the natasha user
ssh natasha@ststor01

# 2️⃣ Go to the destination directory
(Assuming it already exists, as required)
---
cd /usr/src/kodekloudrepos

# 3️⃣ Clone the Git repository
---
git clone /opt/official.git
---
✔ This will create a new directory (usually named official) containing the cloned repository.
✔ No permissions or files outside the repo are changed.

# 4️⃣ Verify the clone (read-only check)
ls
You should see the cloned repository directory listed.

(Optional)
cd official
git status
You should see:
On branch master
nothing to commit, working tree clean
✅ Task completed
Repository cloned successfully
Done as natasha
No unauthorized modifications made
Repository remains intact
================================================================================================
# Q:
[natasha@ststor01 kodekloudrepos]$ git clone /opt/apps.git/
Cloning into 'apps'...
warning: You appear to have cloned an empty repository.
done.
[natasha@ststor01 kodekloudrepos]$ cd apps.git
-bash: cd: apps.git: No such file or directory
[natasha@ststor01 kodekloudrepos]$ cd apps/
[natasha@ststor01 apps]$ ls
[natasha@ststor01 apps]$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
[natasha@ststor01 apps]$ 
ChatGPT said:
You actually did everything correctly 👍
The confusion is only about directory naming, not a mistake.

Let me explain clearly.

What happened (important concept)
🔹 Source repository
/opt/apps.git
This is a bare Git repository

Bare repos usually end with .git

They do not contain a working directory

🔹 After cloning
You ran:

git clone /opt/apps.git/
Git output:

Cloning into 'apps'...
warning: You appear to have cloned an empty repository.
done.
✅ This means:

The repo is empty (no commits yet) → totally OK

Git automatically removed .git from the folder name

So Git created this directory:

apps/
❌ NOT:

apps.git/
Why cd apps.git failed
cd apps.git
-bash: cd: apps.git: No such file or directory
Because Git cloned into apps/, not apps.git/.

Correct directory (you already did it right)
cd apps/
And this output confirms everything is perfect:

git status
On branch master

No commits yet
nothing to commit
✅ This is exactly what an empty repository should look like.

Final verification checklist ✅
✔ Cloned as natasha
✔ Repository cloned to /usr/src/kodekloudrepos
✔ No permissions changed
✔ No files modified
✔ Empty repo warning is expected
✔ Task requirement satisfied

Key takeaway (Linux + Git learning 💡)
something.git → source (bare repo)

something/ → cloned working directory

Empty repo warning ❌ is NOT an error

You completed the task successfully 👏
If you want, I can also explain:

bare repo vs normal repo

why DevOps teams use /opt/*.git

how this appears in real DevOps interviews

Just tell me 🙂

You said:
[natasha@ststor01 apps]$ history
    1  cd /usr/src/kodekloudsrepos
    2  cd /usr/src/kodekloudsrepos/
    3  cd /usr/src/kodekloudrepos/
    4  ls
    5  git clone /opt/apps.git/
    6  cd apps.git
    7  cd apps/
    8  ls
    9  git status
   10  history
[natasha@ststor01 apps]$ 
ChatGPT said:
Perfect — thanks for sharing the command history 👍
Let’s review it carefully and confirm your task status.

✅ History review (line by line)
1  cd /usr/src/kodekloudsrepos
2  cd /usr/src/kodekloudsrepos/
🔸 These paths were slightly incorrect (kodekloudsrepos vs kodekloudrepos),
but no changes were made, so no harm done.

3  cd /usr/src/kodekloudrepos/
✅ Correct destination directory as per the requirement.

4  ls
5  git clone /opt/apps.git/
✅ Repository cloned successfully
⚠️ Warning about empty repository is expected and acceptable

6  cd apps.git
❌ This failed (expected)
➡️ Git clones apps.git into a directory named apps/, not apps.git/

7  cd apps/
8  ls
9  git status
✅ Correct directory
✅ Git repository is clean
✅ No commits yet (empty repo → correct)

10 history
📌 Just showing the history (good for verification)

🎯 Final verdict
✅ TASK COMPLETED SUCCESSFULLY

You fully met all requirements:

✔ Used natasha user
✔ Cloned repo from /opt/apps.git
✔ Target directory: /usr/src/kodekloudrepos
✔ No permission changes
✔ No unauthorized modifications
✔ Repository integrity preserved

🧠 Important DevOps/Linux takeaway
Bare repo: /opt/apps.git

Cloned working copy: apps/

Empty repo warning ≠ error

.git suffix is not used for the working directory

This is exactly how it should look in real DevOps environments 💯