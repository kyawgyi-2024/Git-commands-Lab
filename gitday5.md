# Git Day-5 : Delete Git Branch
# Q.
The Nautilus developers are engaged in active development on one of the project repositories located at /usr/src/kodekloudrepos/cluster. During testing, several test branches were created, and now they require cleanup. Here are the requirements provided to the DevOps team:
On the Storage server in Stratos DC, delete a branch named xfusioncorp_cluster from the /usr/src/kodekloudrepos/cluster Git repository.

Steps to Delete the Branch
Log in to the Storage server

# ssh <storage-server>
Navigate to the Git repository

- cd /usr/src/kodekloudrepos/cluster
Verify existing branches (optional but recommended)

- git branch
Delete the local branch

- git branch -d xfusioncorp_cluster
If Git refuses because the branch is not fully merged, force delete it:

- git branch -D xfusioncorp_cluster
Confirm the branch is removed

- git branch
Summary (One-line command)
cd /usr/src/kodekloudrepos/cluster && git branch -d xfusioncorp_cluster
If you also need to delete the remote branch, tell me and I’ll guide you 👍

--------------------------------------------------------------------------------------------------------
[root@ststor01 cluster]# git branch
  master
* xfusioncorp_cluster
[root@ststor01 cluster]# git branch -d xfusioncorp_cluster
error: cannot delete branch 'xfusioncorp_cluster' used by worktree at '/usr/src/kodekloudrepos/cluster'
[root@ststor01 cluster]# git branch -D xfusioncorp_cluster
error: cannot delete branch 'xfusioncorp_cluster' used by worktree at '/usr/src/kodekloudrepos/cluster'
[root@ststor01 cluster]# 
-----------------------------------------------------------------------------------------------------

* xfusioncorp_cluster   ← currently active branch
So Git blocks deletion.

✅ Correct Fix (Step-by-step)

# 1️⃣ Switch to another branch (master)
git checkout master

Confirm:
git branch
You should see:
* master
  xfusioncorp_cluster

# 2️⃣ Delete the branch now
git branch -D xfusioncorp_cluster

# 3️⃣ Verify deletion
git branch

Expected output:
* master

✅ One-shot solution
git checkout master && git branch -D xfusioncorp_cluster
🔑 Key Concept (Important for DevOps interviews)
❌ You cannot delete a branch that is currently checked out
✅ You must switch to another branch first