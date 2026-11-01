### 1. What is Git Merge?

Git merge is a command used to integrate independent commit histories from one branch into another (for example, combining changes from a feature branch into `main`).

---

### 2. What is a Fast-Forward Merge?

A fast-forward merge occurs when the target branch has no new commits since the feature branch was created. Git simply moves the branch pointer forward to match the latest commit of the feature branch without creating a separate merge commit.

---

### 3. What is a Three-Way Merge?

A three-way merge occurs when both the source and target branches have diverged with independent commits. Git evaluates three snapshots—the common ancestor commit, the tip of the current branch, and the tip of the incoming branch—to combine the changes.

---

### 4. What is a Merge Commit?

A merge commit is a dedicated commit automatically created by Git during a non-fast-forward or three-way merge. It has two parent commits and ties the histories of both branches together.

---

### 5. What causes Merge Conflicts?

Merge conflicts happen when Git attempts to merge two branches that modified the exact same line of a file differently, or when one branch deleted a file that another branch modified. Git cannot automatically determine which version to keep.

---

### 6. How do you resolve Merge Conflicts?

1. Open the conflicted files and locate the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
2. Manually edit the file to keep the desired code and remove all conflict markers.
3. Stage the resolved files using `git add <file>`.
4. Finalize the resolution by running `git commit`.

---

### 7. What is Git Rebase?

Git rebase takes the commits from your current branch and replays them on top of another base branch. It rewrites commit history by generating new commit hashes, resulting in a single continuous line of work.

---

### 8. Difference between Merge and Rebase?

* **Merge:** Preserves the exact chronological history and branch context by creating a merge commit, leaving original commit hashes unchanged.
* **Rebase:** Rewrites project history by moving your feature commits onto the tip of the target branch, creating a clean, linear history without extra merge commits.

---

### 9. Why should Rebase not be used on shared branches?

Rebase rewrites commit history and generates new commit hashes. If other developers are basing their work on commits you rebase and force-push to a public branch, their local histories will diverge, causing synchronization errors and broken workflows (the "Golden Rule of Rebase").

---

### 10. What is a Linear Git History?

A linear Git history is a commit history where every commit follows in a straight sequence, one after another, without branching forks or dedicated merge commits.

---

### 11. How do Pull Requests help teams?

* **Code Review:** Allows peers to review and approve changes before code reaches critical branches.
* **Automated Testing:** Triggers CI/CD pipelines to build, test, and scan code automatically.
* **Discussion & Audit:** Provides a central record of discussions, requirements, and testing notes for future audits.

---

### 12. Why is Merge safer for team collaboration?

Merge is non-destructive. It does not rewrite existing commit hashes or alter historical commits. Even if a mistake occurs during resolution, the original timeline and individual commit contexts remain intact.

---

### 13. What command displays all branches graphically?

```bash
git log --oneline --all --graph

```

---

### 14. What command deletes a local branch?

* **Safe delete (only if already merged):**
```bash
git branch -d <branch-name>

```


* **Force delete (unmerged changes):**
```bash
git branch -D <branch-name>

```



---

### 15. In a DevOps CI/CD workflow, when would you prefer Rebase over Merge?

Rebase is preferred on local or short-lived feature branches before opening or merging a Pull Request (often via GitHub's "Squash and Rebase" feature). It keeps the main pipeline history clean, ensures individual CI builds run cleanly on top of the latest trunk code, and makes rollbacks or `git bisect` debugging faster.


