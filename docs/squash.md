# Git Squash – Feature Branch to Pull Request (Professional Reference)

## Purpose
This document explains **when**, **why**, and **how** to squash Git commits in a
**professional, real-world workflow** where:
- `main` is a protected branch
- Direct push/merge to `main` is not allowed
- Code is merged via Pull Requests (PRs)

---

## Core Rule (Most Important)
> **Do NOT rewrite Git history unless your team or reviewer explicitly asks.**

Rewriting history is normal on **feature branches**, but never on `main`.

---

## Industry-Standard Workflow (Most Common)

1. Create a feature branch from `main`
2. Make multiple commits during development
3. Push the feature branch
4. Open PR → `feature` → `main`
5. Reviewer approves
6. Use **Squash & Merge**
7. `main` ends up with **ONE clean commit**

✔ Feature branch history can be messy  
✔ `main` branch history must be clean

---

## When You SHOULD Squash Locally

Squash your commits **before opening a PR** only if:

- Team guidelines require it
- Repository enforces **linear history**
- Reviewer asks: *“Please squash your commits”*
- You want a very clean PR commit list

If none of the above → **do NOT squash locally**

---

## When You SHOULD NOT Squash

- Working with others on the same feature branch
- Team did not ask for it
- Repository already uses **Squash & Merge**
- You are unsure about force-pushing

---

## Commands: Squashing Feature Commits

### Step 1: Ensure you are on the feature branch
```bash
git checkout feature

git rebase -i main

pick   <old_commit> message
pick   <new_commit> message

pick   09c0bad feature 1.1
squash c706680 feature 1.2

the below is wrong
squash 09c0bad feature 1.1
pick   c706680 feature 1.2

after :wq enter 

another window add the commit and enter 

push to origin
