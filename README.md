# DevOps swiggy-clone Project – Git Branching & Workflow

This project demonstrates Git best practices for a DevOps workflow using **branching**, **feature branches**, **pull requests**, and **merges**.  
We used a Swiggy-like project setup to practice.

---

## 🔹 Branching Strategy

- **main** → Stable production-ready branch  
- **dev** → Development/integration branch  
- **feature-\*** → Feature-specific branches  

Example:
- `feature-docker`
- `feature-swiggy-setup`

---

## 🔹 Step 1: Initialize Git Repository

```bash
git init
git remote add origin https://github.com/<username>/devops-project.git
git branch -M main
git push -u origin main
```

## 🔹 Step 2: Create Development Branch
```bash
git checkout -b dev
git push -u origin dev
```
## 🔹 Step 3: Create Feature Branches
```bash
# Docker feature
git checkout -b feature-docker
git push -u origin feature-docker

# Swiggy setup feature
git checkout -b feature-swiggy-setup
git push -u origin feature-swiggy-setup
```
## 🔹 Step 4: Add Files & Commit Changes
```bash
git add .
git commit -m "Added Swiggy project setup files"
git push origin feature-swiggy-setup
```
🔹 Errors Faced & Fixes
warning: in the working copy of 'Dockerfile', LF will be replaced by CRLF...
✅ Fix:
```bash
git config --global core.autocrlf false
git rm --cached -r .
git reset --hard
```
🔹 to know current branch
```bash
git branch
```
## 🔹 Step 5: Pull Request Workflow

- Push feature branch to GitHub
- Open Pull Request (PR) from feature-* → dev
- Team reviews code
- If approved → Click Merge Pull Request
![AWS EC2 Security Group](images/pr.png)


## 🔹 Step 6: Merge Feature → Dev

# On GitHub via PR
feature-swiggy-setup → dev


## 🔹 Step 7: Merge Dev → Main (Production)
Once testing in dev is complete:
![AWS EC2 Security Group](images/ci-cd-fail-2.png)
![AWS EC2 Security Group](images/ci-cd-fail-3.png)

- After testing and fixing eror

![AWS EC2 Security Group](images/ci-cd-pass.png)
![AWS EC2 Security Group](images/ci-cd-pass-2.png)


## 🚀 Merging Tested Code from dev to main with Tags
- Once all features are tested in the dev branch, follow these steps to merge them into main and create a release tag:
```bash
# 1. Switch to main branch
git checkout main

# 2. Pull the latest changes
git pull origin main

# 3. Merge tested code from dev branch
git merge dev

# 4. Resolve any merge conflicts if they appear, then commit.

# 5. Push merged changes to GitHub
git push origin main

# 6. Create a version tag (example: v1.0.0)
git tag -a v1.0.0 -m "Release v1.0.0 - stable tested version"

# 7. Push tags to GitHub
git push origin v1.0.0
```
![AWS EC2 Security Group](images/final.png)

# On GitHub via PR
- dev → main
- This makes the project stable and production-ready.
- # Merge workflow (via GitHub PR)
- feature-branch → dev → main
- ✅ Final Workflow Diagram
```css
 feature-docker ─────┐
 feature-swiggy-setup ──┐
                       │
                       ▼
                     [ dev ]
                       │
                       ▼
                     [ main ]
```
                     

### Notes
- Always create new features in feature-* branches.
- Merge to dev after review.
- Merge dev → main only after testing.
- .gitignore is used to avoid unnecessary files.
- Tags can be used for versioning:
```bash
git tag v1.0
git push origin v1.0
```







