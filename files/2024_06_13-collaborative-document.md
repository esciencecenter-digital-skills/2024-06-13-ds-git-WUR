![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document

2024-06-13 Collaborative version control with git and GitHub (2024-06-13-ds-git-WUR)

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

This is the Document for today: [link](https://tinyurl.com/git-wur-2024-06-13)
https://tinyurl.com/git-wur-2024-06-13


##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
 For more details, see [here](https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html).

Want to report a Code of Conduct incident and you prefer to do it anonymously? You can do it [here](https://goo.gl/forms/KoUfO53Za3apOuOK2).

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, just raise your hand.

If you need help from a helper, place a pink post-it note on your laptop lid. A helper will come to assist you as soon as possible.

## 🖥 Workshop website

[Link](https://esciencecenter-digital-skills.github.io/2024-06-13-ds-git-WUR)

🛠 Setup

We will assume everyone can access the command line on their laptop and managed to follow these [**setup instructions**](https://esciencecenter-digital-skills.github.io/2024-06-13-ds-git-WUR/#setup).

Please put a pink post-it note on you laptop lid, if you need a bit more help with the setup.

## 👩‍🏫👩‍💻🎓 Instructors

Sander van Rijn, Olga Lyashevska

## 🧑‍🙋 Helpers

Lucas Esclapez, Johan Hidding

## 🗓️ Agenda


|  Time | Topic                                    |
| -----:|:---------------------------------------- |
| 09:00 | Welcome and icebreaker                   | 
| 09:15 | Workshop Introduction                    |
| 09:30 | Introduction to version control with Git |
| 10:20 | **Coffee break**                         |
| 10:35 | Tracking changes and exploring history   |
| 11:30 | **Coffee break**                         |
| 11:45 | Ignoring things, remotes, and conflicts  |
| 12:30 | **Lunch Break**                          |
| 13:30 | Collaboration with Git and GitLab        |
| 14:15 | **Coffee break**                         |
| 14:30 | Collaboration with Git and GitLab        |
| 15:15 | **Coffee break**                         |
| 15:30 | Collaboration with Git and GitLab        |
| 16:15 | Wrap-up                                  |
| 16:30 | END                                      |


## 🏢 Location logistics
* Coffee and toilets
* Emergency exit
* Wifi

## 🎓 Certificate of attendance
If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## 🔧 Exercises

### 1. Places to create Git repositories

Along with tracking information about planets (the project we have already created), Dracula would also like to track information about moons. Despite Wolfman’s concerns, Dracula creates a moons project inside his planets project with the following sequence of commands:

```bash
$ cd ~/Desktop   # return to Desktop directory
$ cd planets     # go into planets directory, which is already a Git repository
$ ls -a          # ensure the .git subdirectory is still present in the planets directory
$ mkdir moons    # make a subdirectory planets/moons
$ cd moons       # go into moons subdirectory
$ git init       # make the moons subdirectory a Git repository
$ ls -a          # ensure the .git subdirectory is present indicating we have created a new Git repository
```

Is the `git init` command, run inside the `moons` subdirectory, required for tracking files stored in the `moons` subdirectory?

#### Solution

Here we were creating a repo in a repo. Git will trip over this. Fix this by removing the unwanted `.git` directory.

```bash
$ pwd
.../planets/moons
$ ls -a
.git
$ rm -rf .git
```

### 2. Committing Multiple Files
Remember that the staging area can hold changes from any number of files that you want to commit as a single snapshot.

1. Add some text to ``mars.txt`` noting your decision to consider Venus as a base
2. Create a new file ``venus.txt`` with your initial thoughts about Venus as a base for you and your friends
3. Add changes from both files to the staging area, and commit those changes.

#### Solution

```bash
$ echo "We should consider Venus as an alternative target for our base" >> mars.txt
$ echo "Venus may be a bit too hot for Wolfman" > venus.txt
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   mars.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	venus.txt

no changes added to commit (use "git add" and/or "git commit -a")
$ git add mars.txt venus.txt
$ git commit -m "consider Venus as an alternative target"
```

Alternatively you can say

```
git add .
```

to add all files mentioned in the status overview to the staging area. However, be careful! In many cases there will be files there that you don't want to add, like build artifacts or other temporary files. Always check with `git status` what would be added.


### 3. Recovering Older Versions of a File
Jennifer has made changes to the Python script that she has been working on for weeks, and the modifications she made this morning “broke” the script and it no longer runs. She has spent ~ 1hr trying to fix it, with no luck…

Luckily, she has been keeping track of her project’s versions using Git! Which commands below will let her recover the last committed version of her Python script called `data_cruncher.py?` Multiple options might be correct:

1. `$ git restore .`
2. `$ git restore data_cruncher.py`
3. `$ git restore -s HEAD~1 data_cruncher.py`
4. `$ git restore -s <unique ID of last commit> data_cruncher.py`

#### Solution
We assume tha Jennifer has not touched the commit history. So she'd want to restore from the latest committed version: `git restore data_cruncher.py`. Answer 4 does the same, but with more typing.


### 4. Working as a project collaborator (in pairs)

Do this exercise in pairs.

#### Part 1
- PERSON A: Create an issue in the repository
- PERSON B: Clone this repository to your system
- PERSON B: Create a new branch
- PERSON B: Make the changes requested in the issue
- PERSON B: Push the changes to the remote repository on GitHub
- PERSON B: submit a Pull Request, refer to the issue (e.g. "Closes #1")

#### Part 2
- PERSON A: review the Pull Request
- PERSON B: address the comments
- PERSON A: approve the Pull Request
- PERSON B: merge the Pull Request

### 5. Working as an external contributor (in pairs)

#### Part 1
- PERSON A: Create an issue in Person B's repository
- PERSON A: Fork the repository to their own (= Person A's) account
- PERSON A: Clone the repository, make changes, push them back to the fork
- PERSON A: Submit a Pull Request from the fork to the original repository

#### Part 2
- PERSON B: Make a change in the original repository in the same place as person A's proposed changes
- PERSON A: Solve the merge conflict in the Pull Request
- PERSON B: Review/Approve the Pull Request
- PERSON B: merge the Pull Request

## 🧠 Collaborative Notes

:::warning
Sometimes the bash commands have a `$` sign in front of them. This is an indicator that we show a command and then its expected output. The `$` is not part of the command!

Similarly, the expected output sometimes contains elipsis `...` to indicate output that will differ per person.
:::

### Configuring

```bash
git config --global --user.name "Your Name"
git config --global --user.email "your.email@address.nl"
```

Edit your config

```bash
git config --global --edit
```

### Creating a repository

Create a directory for your repository:

```bash
mkdir planets
```

Enable git version tracking

```bash
cd planets
git init
```

Check that the directory is now tracked by git.

```bash
ls -a
```

should give as output:

```
.git
```

### Tracking Changes

We create a file in `nano`.

```bash
$ pwd
.../planets
$ nano mars.txt
```

alternatively

```bash
echo "Cold and dry but everything is my favourite color" > mars.txt
```

Check the contents of the new file

```bash
$ cat mars.txt
Cold and dry but everything is my favourite color
```

If we check the status

```bash
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	mars.txt

nothing added to commit but untracked files present (use "git add" to track)
```

We see that git notices the changes, but isn't doing anything (Untracked files).

Then add the changes to the **staging area**.

```bash
git add mars.txt
```

```bash
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   mars.txt
```

Now changes are in the staging area (to be committed), but not yet committed.

```bash
$ git commit -m "start notes on Mars as a base"
[main (root-commit) 2dafacb] start notes on Mars as a base
 1 file changed, 1 insertion(+)
 create mode 100644 mars.txt
```

```bash
$ git status
On branch main
nothing to commit, working tree clean
```

To see the history use `git log`

```bash
$ git log
commit 2dafacb0e8e1327cb49cced4c26b902a5b3cacfa (HEAD -> main)
Author: ...
Date:   Thu Jun 13 10:53:17 2024 +0200

    start notes on Mars as a base
```

:::info
The commands `git add`, `git commit`, `git status` and `git log` cover 90% of your time with git. Congratulations! :beers:
:::

#### Empty commits
Lets make some more changes

```bash
$ echo "The two moons may be a problem for Wolfman" >> mars.txt
$ cat mars.txt
Cold and dry but everything is my favourite color
The two moons may be a problem for Wolfman
```

We can inspect changes with `git diff`.

```bash
$ git diff
diff --git a/mars.txt b/mars.txt
index 5b085f5..241f2b8 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,2 @@
 Cold and dry but everything is my favourite color
+The two moons may be a problem for Wolfman
```

And `commit` again.

```bash
$ git commit -m "Add concerns about effect of Mars moons on Wolfman health"
...
no changes added to commit (use "git add" and/or "git commit -a")
```

Oops! We still need to `add` the changes. (Use your arrow keys so you don't have to retype the `git commit` command)

```bash
$ git add mars.txt
$ git commit -m "Add concerns about effect of Mars moons on Wolfman health"
[main ad1af74] Add concerns about effect of Mars moons on Wolfman health
 1 file changed, 1 insertion(+)
```

#### `diff --staged`

Make some more changes:

```bash
echo "But the Mummy will appreciate the low humidity" >> mars.txt
```

```bash
$ git add mars.txt
$ git diff
```

Nothing!

If we want to see changes in the staging area, wee need to add `--staged` flag to the `git diff` command.

```bash
$ git diff --staged
diff --git a/mars.txt b/mars.txt
index 241f2b8..5d3454e 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,2 +1,3 @@
 Cold and dry but everything is my favourite color
 The two moons may be a problem for Wolfman
+But the Mummy will appreciate the low humidity
```

```bash
git commit -m "Discuss concerns about Mars climate for Mummy"
```

### Viewing history

To see all changes since some previous commit:

```
git diff HEAD~3
```

It is not always so nice to have to count back the number of commits. In `git log` we can see our commit history including a special key for every commit:

```txt
commit b16a45da05d745c1389f157d8ce20725a0b82d77 (HEAD -> main)
Author: ...
Date:   Thu Jun 13 11:51:11 2024 +0200

    consider venus

commit eed5530df68c45914cf1b6d811f399f89c04ef52
Author: ...
Date:   Thu Jun 13 11:11:36 2024 +0200

    Discuss concerns about Mars climate for Mummy

commit ad1af74d41f48fc72ea161644b999206aefdbdbe
Author: ...
Date:   Thu Jun 13 11:03:35 2024 +0200

    Add concerns about effect of Mars moons on Wolfman health

commit 2dafacb0e8e1327cb49cced4c26b902a5b3cacfa
Author: ...
Date:   Thu Jun 13 10:53:17 2024 +0200

    start notes on Mars as a base

```

Now we can use `git show <commit-id>` to show the changes made in every commit, and `git diff <commit-id>` to see the aggregated changes since that commit.

#### Accidental changes

Make an accident happen:

```bash
$ echo "blurp" >> mars.txt
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Git suggests several ways to continue: adding, but also restoring.

```bash
$ git restore mars.txt
$ git status
On branch main
nothing to commit, working tree clean

```

This throws away our changes! No undo is possible for changes that are not tracked.

We can also restore a version from a different commit:

```bash
$ git restore -s HEAD~2 mars.txt
$ cat mars.txt 
Cold and dry but everything is my favourite color
The two moons may be a problem for Wolfman
```

:::info
Git's `restore` command functions as if you made the changes yourself (i.e. in an editor). The chain of commits is unaffected. Only the file that you restored is changed.
:::

Restore the file back to latest version:

```bash
$ git restore mars.txt
$ git status
On branch main
nothing to commit, working tree clean

```


#### Search for a specific commit

You can search for a specific commit by using the following command:

```bash
git log --grep Wolfman
```

It will return all commits in which word "Wolfman" is used. 


### Ignoring changes

Suppose our code creates a plot that we don't want tracked in version control. We'll simulate this by `touch`ing a (creating an emtpy) PNG file.

```bash
$ touch data.csv
$ touch my_awesome_plot.png
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	data.csv
	my_awesome_plot.png

nothing added to commit but untracked files present (use "git add" to track)

```

We'd like to ignore the PNG file now. We create a `.gitignore` file.

```bash
$ echo "*.png" >> .gitignore
$ echo "*.csv" >> .gitignore
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.gitignore

nothing added to commit but untracked files present (use "git add" to track)

```

The `.gitignore` file should be tracked!

```bash
$ git add .gitignore
$ git commit -m 'create .gitignore to ignore PNG and CSV files'
$ git status
On branch main
nothing to commit, working tree clean

$ ls
data.csv  mars.txt  my_awesome_plot.png  venus.txt

```

See, the files are still there, but they're not under version control.

### Remotes

There are several commercial parties offering remote storage for git: Github, Gitlab, BitBucket, etc. Luckily, the WUR supplies storage as well at `git.wur.nl` (using Gitlab interface). Most web interfaces will have very similar functionality, but buttons and names can be slightly different.

We add the remote:

```bash
git remote add origin <url>
```

```bash
$ git push origin main
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 8 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (16/16), 1.43 KiB | 489.00 KiB/s, done.
Total 16 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
To git.wur.nl:.../mars.git
 * [new branch]      main -> main

```

To retrieve these files on a different computer use `git clone`

```bash
git clone <url>
```

Updating to the latest version from the remote:

```bash
git pull origin main
```

### Social Git

When working with multiple persons on a single project, it is often good to work in multiple **branches**.

Create a branch

```bash
git branch featureAddSum
```

Switch branch

```bash
git switch featureAddSum
```

Make your changes and `git add`, `git commit` like before. Now when pushing to the remote make sure to mention the correct branch:

```bash
git push origin featureAddSum
```

#### Merging branches locally
When you are ready to merge, you need to merge back main into the feature branch (to make sure you pull all changes that have been made to `main` since you branched).

```bash
git merge main
```

Then when the feature branch is up-to-date with `main`, we can merge the feature branch into `main`.

```bash
git switch main
git merge featureAddSum
git push origin main
```

#### Branching strategies

For most cases, with small teams, we advise the branching strategy known as [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow). This involves a `main` branch, `develop` branch and a set of feature branches, branching off `develop`. Whenever you are happy with the state of things in `develop` you can merge it with `main`. This way you will always have a good version in `main`.


### Git cheatsheet:
 - ```git init``` : initialize a git repository, creating a hidden .git folder in the current folder.
 - ```git status``` : report the status of the current repository, which `branch` we are on, listing untracked/changed files.
 - ```git log``` : print the git commit history, from the most recent (top) to the oldest.
 - ```git add``` : add file(s) (new or changed) to the staging area.
 - ```git commit``` : move file(s) from the stagging area to the repository.
 - ```git diff``` : show the difference(s) between the current version of your file(s) and the one in the staging area (for all tracked files).
 - ```git diff --staged``` : show the difference(s) between the staging area and the repository for all the staged files.
 -  ```git diff <hash>``` : show the difference(s) between the current version of your file(s) and the version in the repository at the commit specified by `<hash>`
 -  ```git restore <file>```: restore `<file>` to the last version of the file present in the repository. WARNING: all changes will be lost.
 -  ```git restore -s <hash> <file>```: restore `<file>` to the version present in the repository on the commit specified by `<hash>`. WARNING: all changes will be lost.


## 📚 Resources
* Upcoming workshops: https://www.esciencecenter.nl/events/?f=workshops
* Schedule of all workshops in the year: https://www.esciencecenter.nl/digital-skills/ (scroll down)
* Subscribe to our newsletter (stay updated on upcoming workshops): eepurl.com/dtjzwP
* NL RSE community: https://nl-rse.org
* Slides: https://lyashevska.github.io/ds-cr-slides/
* Really nice free book: https://git-scm.com/book/en/v2
* Blog about atomic commits: https://blog.esciencecenter.nl/the-utopic-git-history-d44b81c09593
* Git cheat sheet: https://education.github.com/git-cheat-sheet-education.pdf
* A logical, reasonably standardized but flexible project structure for data science.: https://cookiecutter-data-science.drivendata.org/
* Lesson material collaborating in the same repository https://coderefinery.github.io/git-collaborative/same-repository/
* Lesson material collaborating to a repository from someone else: https://coderefinery.github.io/git-collaborative/forking-workflow/
* A nice blogpost about atomic commits: https://blog.esciencecenter.nl/the-utopic-git-history-d44b81c09593
* 
