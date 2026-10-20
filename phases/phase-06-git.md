# Phase 6: Git and GitHub

This week you learn the tool every developer and security engineer uses to track code: Git. You start with the basics (init, add, commit, log), then move to branching, merging, GitHub, README files, and pull requests. By day 63 you will have a polished GitHub profile holding your own scripts, which is exactly what employers look at.

## Day 57: Version control basics (init, add, commit, log)
- **Learn:** Version control is a system that records every change to your files so you can look back, undo mistakes, and see who changed what and when. Git is the most popular version control tool, and it works locally on your machine with no account needed.
- **Do:** Create a folder called git-practice, run git init inside it, add a text file with git add, save it with git commit -m "first commit", then view your history with git log. Commands: mkdir git-practice && cd git-practice && git init, echo "hello git" > notes.txt, git add notes.txt, git commit -m "first commit", git log.
- [ ] Done: You see your commit listed when you run git log inside the git-practice folder.

## Day 58: Branching, merging, and fixing conflicts
- **Learn:** A branch is a separate line of work that lets you try changes without touching the main code. When you are done you merge the branch back, and if both sides changed the same lines, Git asks you to resolve the merge conflict by hand.
- **Do:** In your git-practice folder, create a branch with git branch feature, switch to it with git checkout feature, edit notes.txt and commit the change. Switch back with git checkout main (or master), edit the same line of notes.txt differently and commit. Then run git merge feature, open the conflict markers (<<<<<<<, =======, >>>>>>>) in notes.txt, pick the lines you want, and run git add notes.txt and git commit to finish the merge.
- [ ] Done: git log --graph --oneline shows your branch and merge, and notes.txt has no conflict markers left.

## Day 59: Remotes, push, pull, and your first GitHub repo
- **Learn:** A remote is a copy of your repo stored on a server like GitHub, so your work is backed up and shareable. You push to send your commits to the remote, and you pull to download commits from it.
- **Do:** Create a free account at github.com, click New repository, name it git-practice, and leave it empty. Back in your terminal inside git-practice, link it with git remote add origin https://github.com/YOUR-USERNAME/git-practice.git, then run git push -u origin main (use master if that is your branch name) and type your login when asked. Refresh the GitHub page to see your files.
- [ ] Done: Your git-practice repo is visible on your GitHub profile with your commits listed.

## Day 60: .gitignore and a good README in markdown
- **Learn:** A .gitignore file lists patterns of files Git should never track, like passwords, logs, or editor temp files. A README.md is the front page of your repo written in markdown, and it is the first thing anyone reads to understand your project.
- **Do:** In your git-practice folder, create a .gitignore file containing the lines *.log, secrets.txt, and .vscode/. Then write a README.md with a title line (# git-practice), a short description of what the repo is for, and a section showing the commands you used this week. Commit and push both files, then check that they look good on the GitHub repo page.
- [ ] Done: Your GitHub repo page shows a formatted README and the ignored file types are not uploaded.

## Day 61: Learn Git branching with the learngitbranching game
- **Learn:** Today is pure practice: the interactive game at https://learngitbranching.js.org teaches branching and merging visually, level by level, and it is the fastest way to make the commands stick.
- **Do:** Open https://learngitbranching.js.org and play through the entire "Main" sequence of levels (the first group, ending with "Multiple parents" or the last main level shown). Type every command yourself in the game terminal instead of reading the answer cards. If you finish early, start the first two "Remote" levels too.
- [ ] Done: All Main levels show as completed in the game, and you can explain what git rebase and git cherry-pick do without checking notes.

## Day 62: Polish your GitHub profile and publish your work
- **Learn:** A strong GitHub profile works like a portfolio: a profile README introduces you, and pinned repos show your best projects first, which is what hiring managers open.
- **Do:** Create a new repo named exactly like your GitHub username (YOUR-USERNAME/YOUR-USERNAME), add a README.md with a short bio, what you are learning, and links to your repos. Then pin up to 6 repos on your profile (Profile, Customize your pins). Finally, create a new public repo called cyber-scripts, push your Python scripts and study notes from this 90-day plan into it with a proper README, and push your updated work from the whole week.
- [ ] Done: Your GitHub profile shows a profile README and your cyber-scripts repo is public, pinned, and has a clear README.

## Day 63: Collaboration with forks and pull requests
- **Learn:** A fork is your personal copy of someone else's repo, and a pull request (PR) is how you propose your changes back to the original project. This is how all open-source collaboration works.
- **Do:** Pick one of these two: (1) fork a small open-source repo (for example one with a typo or broken link in its docs), clone your fork, create a branch with git checkout -b fix-typo, make the fix, push the branch, and open a pull request from your fork to the original repo; or (2) on your own cyber-scripts repo, create a branch, add a new script or improve a README, push the branch, and open a pull request to merge it into main yourself. Write a clear PR title and a one-line description of the change.
- [ ] Done: A pull request exists for your change (merged or awaiting review) and you can explain the fork, branch, PR, merge steps in your own words.
