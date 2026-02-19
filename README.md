
# merge-pull-request-lab
> cis 486 teaching lab for pull request and merge scenarios

## Instructions

1. **Fork this repository** (creates a copy in your GitHub account)
2. Complete all three parts below, following the steps for each:
   - Creating branches (always from `main`)
   - Adding/editing files
   - Generating PRs and merges (as specified)
3. Submit your forked repo link.

---

## Part 1: GitHub PR/Merge

For each exercise:
- Complete all exclusively on GitHub (no local .git)
  - no "issues" required for Part 1, let's just get in the flow. 
- Start from the `main` branch. Create a new branch (e.g., `pr1`).
- Complete the task (add/edit files as described).
- Commit your changes.
- Open a Pull Request (PR) to merge your branch into `main`.
- Merge the PR via GitHub UI.
- Delete/prune the branch after merging.

Examples:

### Exercise 1️⃣ `pr1` | edd a new file (no conflict)
- Create branch `pr1` from `main`.
- Add a new file: `merge.md` 
- Add some text, like `adding all my code to this project, your name`
- Commit it, 
- open a PR (either from the notification or on the navbar), 
- merge it, 
- delete the branch
- ✅ is your `merge.md` in your main branch? 

### Exercise 2️⃣ `pr2` | edit an existing file (no conflict)
- Create branch `pr2` from `main`.
- Edit `merge.md`: add a new line underneath existing text 
  - Important: Don't move/change existing lines => creates a conflict
  - Just go to the bottom of the file and put your new lines there
  - Something like: `adding my code to this existing code` 
- Repeat: Commit, PR, merge, delete branch.
- ✅ is your `merge.md` in your main branch with the new text? 

### Exercise 3️⃣ `pr3` | edit an existing file (create a conflict)
- Create branch `pr3` from `main`.
- Edit `merge.md`, this time let's shake things up. 
  - change a few things around.
  - edit the text on an existing line. 
  - add a new line at the top. 
- Do it again: Commit, PR, ...
  - this time, you will have conflicts, 
  - click on "Web Editor" to resolve them
- Remove the `<<<< HEAD ... ====== >>>>` GitHub merge conflict syntax.
- ensure you keep the text you want, how you want it
  - i.e., no repetition, all clean.   
  - commit it (commits back to `pr3` and then is all up to date)
- resume your process:
  - merge, delete branch.

### Wrap up. 
- great! Now you've got 3 PR/merges under your belt. 
- a Pull Request (pr, PR) is a GitHub thing (not local `.git`)
- a pr is a "coversation" about a merge
- this is a precurosr to a proposed merge "event"
- so...

```
pr === conversation 

merge === event
```

---

## Part 2: Local Git Branches & PRs (based on GitHub Issues)

For each exercise:
- Refer to the original LAB repo GitHub Issues for instructions (each issue will describe the task).
- on your fork, on GitHub, re-create each issue 
- Clone your fork locally.
- Start from `main`. Create a new branch named for the issue (e.g., `iss1` for Issue #1).
- Complete the task described in the issue (add/edit files as specified).
- Commit and push the branch to GitHub.
- Open a PR on GitHub to merge your branch into `main`.
- on the PR, the first text area (not a comment), the first line,
  - type: `closes iss #1` (or whatever the issue number is)
- Merge the PR via GitHub.
- Delete/prune the branch after merging.
- Confirm that the issue is closed
  - nav to the issue (e.g., `iss1`)
  - it should be closed AND have be linked to the PR
  - if not, manually link it & close it! 

### Exercises 4️⃣ 5️⃣ 6️⃣
- Refer to https://github.com/una-cis-376/merge-pull-request-lab/issues

---


## Part 3: Local Git Merges & Rebase (No PR)

Branches: `m1`, `m2`, ...

### Exercise 7: Git Merge (No Conflict)

#### On your local dev box

1. Make sure you are on main and up to date:
  ```sh
  git checkout main
  git pull
  ```
2. Create a new branch for this exercise:
  ```sh
  git checkout -b m1
  ```
3. Add a new file called `merge3.md` and add this text:
  ```
  this is code from branch m1 to merge into main
  ```
4. Stage and commit your changes:
  ```sh
  git add merge3.md
  git commit -m "add merge3.md from m1"
  ```
5. Switch back to main:
  ```sh
  git checkout main
  ```
6. Merge the m1 branch into main:
  ```sh
  git merge m1
  ```
  - This should be a “fast-forward” or clean merge with no conflicts.
  - You’ll see a message about the merge in your terminal.

7. Delete the m1 branch (cleanup):
  ```sh
  git branch -d m1
  ```

#### Insights
- You always merge into the branch you are currently on (here, main).
- The merged code from m1 is now part of main.

---

### Exercise 8: Git Merge (With Conflict) & Resolving in VS Code

> Create and resolve a merge conflict using VS Code.

#### On your local dev box

1. Make sure you are on main and up to date:
  ```sh
  git checkout main
  git pull
  ```
2. Create a new branch for this exercise:
  ```sh
  git checkout -b m2
  ```
3. Edit `merge3.md` by changing the line to:
  ```
  this is new code from branch m2 to conflict with code on main
  ```
4. Stage and commit your changes:
  ```sh
  git add merge3.md
  git commit -m "edit merge3.md from m2"
  ```
5. Switch back to main:
  ```sh
  git checkout main
  ```
6. (Optional) Edit `merge3.md` on main to a different value to ensure a conflict, then commit.

7. Now, try to merge m2 into main:
  ```sh
  git merge m2
  ```
  - You will see a conflict message.

#### Resolving the conflict in VS Code

- Open `merge3.md` in VS Code.
- You’ll see conflict markers:
  ```
  <<<<<<< HEAD
  (main branch code)
  =======
  (m2 branch code)
  >>>>>>> m2
  ```
- Decide which code to keep:
  - “Accept Current Change” = keep what’s on main.
  - “Accept Incoming Change” = keep what’s from m2.
  - Or, manually edit to combine both as needed.
- Save the file after resolving.

#### Finish the merge

1. Stage the resolved file:
  ```sh
  git add merge3.md
  ```
2. Complete the merge with a commit:
  ```sh
  git commit
  ```
3. Delete the m2 branch:
  ```sh
  git branch -d m2
  ```

#### Insights
- “Current Change” = main branch.
- “Incoming Change” = the branch you are merging in (m2).
- You must resolve all conflicts before you can finish the merge.

---

### Exercise 9: Force Overwrite main with a Branch

> Practice force-overwriting main with the contents of another branch (use with caution!).

#### On your local dev box

1. Make sure you are on main and up to date:
  ```sh
  git checkout main
  git pull
  ```
2. Create a new branch for this exercise:
  ```sh
  git checkout -b m3
  ```
3. Edit an existing file (e.g., `merge3.md`) and completely change its contents. For example:
  ```
  This file has been completely overwritten by branch m3.
  ```
4. Stage and commit your changes:
  ```sh
  git add merge3.md
  git commit -m "completely overwrite merge3.md from m3"
  ```
5. Now, force main to match m3:
  - Switch to main:
    ```sh
    git checkout main
    ```
  - Reset main to m3 (this makes your local main match m3 exactly):
    ```sh
    git reset --hard m3
    ```
  - Force-push main to the remote (this will overwrite the remote main branch!):
    ```sh
    git push origin main --force
    ```

#### Insights
- This method will make main exactly match m3, overwriting any changes on main that are not in m3.
- Use with caution—this rewrites history and can affect collaborators.
- The reset is necessary to make your local main branch match the branch you want to force over it.

---

## Wrap Up & Next Steps

- You’ve now practiced basic merges, conflict resolution, and force-overwriting main with a branch.
- good practices, tips
  - always create new branches from `main` (branches from existing issues get your wires crossed!)
  - Clean up branches after merging
  - PR = conversation, Merge = event
  - For merge: “Stand on the branch that will receive the changes.”
  - > When you run git merge, you should first checkout (be “standing on”) the branch you want to update with changes from another branch. The branch you are on is the one that will get the new commits.
- In real-world projects, use force pushes sparingly and communicate with your team.
- Want to learn more? Look up:
  - `git rebase` (replay your branch’s commits on top of another branch for a linear history)
  - `git revert` (undo a commit by creating a new commit)
  - Advanced merge conflict resolution tools in VS Code
  - Branch protection rules on GitHub to prevent force pushes

---


