🔹 Essential Git Commands
Task	Command
Initialize repo	git init
Clone repo	git clone <url>
Add file	git add file.txt
Commit	git commit -m "msg"
Status	git status
Diff before commit	git diff
Diff staged vs last commit	git diff --cached
Check tracked files	git ls-files
Who changed what	git blame file.txt
🔹 Branching & Merging
Command	Use
Create branch	git branch feature1
Switch branch	git checkout feature1 or git switch feature1
Merge branch	git merge feature1
Merge conflict resolve	Edit file → git add . → git commit
🧠 3-Way Merge (Recursive Strategy):
Git compares common ancestor, current HEAD and the incoming branch to merge.

✅ Merge strategies:

recursive (default)

ours – keep current branch

theirs – keep incoming branch

🔹 Git Rebase – Deep Dive
Term	Meaning
Rebase	Reapplies commits from one branch on top of another, linear history.
Interactive Rebase	git rebase -i HEAD~3 – edit, squash, reorder commits.
🧠 Use Rebase When:

Want clean commit history.

Personal branches.

Avoid rebase on main or shared branches.

⚠️ Never rebase shared/public branches — changes history and breaks everyone else's state.

🔁 Literal meaning: Rebase = "base it again on another commit".

🔹 Undoing Changes
Task	Command
Discard unstaged changes	git restore file.txt or git checkout -- file.txt
Unstage a file	git reset file.txt
Discard local commits (soft)	git reset --soft HEAD~1
Discard commits (hard)	git reset --hard HEAD~2
Revert a commit safely	git revert <commit_hash>
🔹 Git Internals & Performance
git status is fast due to file mtime optimizations, index cache, fsmonitor.

Large repos slow down due to lstat() syscall on 100k+ files.

Enable speed-ups:

bash
Copy
Edit
git config feature.manyFiles true
git config core.fsmonitor true
git maintenance start
Use git sparse-checkout for monorepos to checkout only needed folders:

bash
Copy
Edit
git sparse-checkout init --cone
git sparse-checkout set frontend/
🔹 Scenario-based Interview Q&A
Q1. How to revert a specific file to an older commit?
👉 git checkout <commit_hash> -- file.txt
or
👉 git restore --source=<commit_hash> file.txt

Q2. How to squash last 2 commits?

bash
Copy
Edit
git rebase -i HEAD~2
# change "pick" to "squash"
Q3. How to remove remote branch?

bash
Copy
Edit
git push origin --delete feature1
Q4. You accidentally committed secrets, how to remove it?

Use git filter-branch or git filter-repo to rewrite history.

Q5. How to list current Git references?

bash
Copy
Edit
git show-ref
find .git/refs/
🔹 Anti-patterns in Git
Mistake	Why Avoid
Large commits	Hard to review/debug
Committing secrets	Risky & irreversible
Rewriting public history	Breaks collaboration
Not writing commit messages	No traceability
Ignoring .gitignore	Unnecessary files in repo
🔹 Advanced Tips
Concept	Use
.gitattributes	Line endings, diff rules for specific files
git stash	Save changes temporarily
git cherry-pick	Apply specific commit from another branch
git bisect	Find which commit introduced a bug
🔹 Top Interview Questions (2025)
What is the difference between git pull and git fetch?

What happens behind git commit?

How does Git know the last commit SHA?

What’s the difference between git reset, git revert, and git checkout?

What are merge strategies in Git?

What is a 3-way merge?

How do you resolve merge conflicts?

What is interactive rebase and when do you use it?

How do you manage monorepos at scale?

How does git status work under the hood?

Explain .git folder internals.

What is git reflog?

Difference between HEAD, HEAD~1, and origin/main.

What are Git hooks? How can they help DevOps pipelines?

Real-life Git disaster recovery situation and how you fixed it?

🤝 Final Notes
🔄 Practice Git scenarios regularly.

⚠️ Never rewrite public history unless you're sure.

🚀 Keep your history clean. Use rebase for clarity.

📂 Push only required files. Ignore binaries/logs.

🧠 Always write meaningful commit messages.

