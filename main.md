---
marp: true
lang: en-US
title: Commit to Git?
description: A short introduction to version control in computational sciences
theme: example
transition: fade
paginate: true
_paginate: false # No page number on first slide
math: mathjax
author: Julian Karl Bauer
# header:
footer: 04.12.2024, Julian Karl Bauer, Commit to Git?
---

# Commit to Git?

#### A short introduction to version control in computational sciences

<br>
<br>

04.12.2024
Julian Karl Bauer

<!--
Thank you for the kind introduction
and thanks for inviting me.

I really liked the presentation
"Reproducibility and Data Management in Computational Science"
Emil gave in the last Students Chapter.

An important building block for all the things Emil had talked about is version control.
This gave me motivation to kind of recycle a talk on Git basics I gave several years ago.

Probabyl the world changed and all of you have a profound understaning of
what version control is and how to use it.
But I was encouraged, that recaping the basics, might be a thing worth doing.
I have a feeling that the invitation may have raised expectations
that are a little too high among experienced Git users.
Sorry in advance, my talk will be basic.

I will give a rough introduction to basic concepts of version control with Git.
Let's start
-->

---

### What is Git?

<br>

<!-- prettier-ignore-start -->

* The second big project of Linus Torvald (the Linux guy)
* A distributed version control system
* Command line interface (CLI)
* A [content-addressable filesystem][git_internals]

<!-- prettier-ignore-end -->

[git_internals]: https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

<!--

The major question of this talk is:

What is Git?

There are certainly a number of legitimate answers...
For example:
- ...

These answers address different aspects of Git.

The first one obviously tries to create interest by referencing a well-known person.
But it might also refer to the significance of Git.
Like Linux, Git is involved everywhere, once you are able to see it.

The second and third essentially tell you, Git is software
and you can use it from your terminal.
And these are the things we will focus on.
We'll discuss what a distributed version control system is
and how to use it, focusing on the command line interface.

The fourth information is just a reference for those of you
who want to dig deeper into the machinery.
I can't tell you much about it, read it once, forgot it long time ago,
because it is not really essential for a user of Git.

So, let us focus on Git being a version control system
and the command line interface which allows us to use it.

What does version control system mean?

-->

---

### What is version control?

<br>

**Tracking changes** to a **file structure** including **metadata** on

- Who: Author
- When: Timestamp
- Why: Elaboration in commit message

changed something. This **enables structured collaboration** among team members.

<!--
Version control is build to
...

Using version control, you get the
- What (the changes)
- Who (Author) and
- When (Timestamp)
for free and automated.

This helps you to focus on the Why,
which commonly is ecnoded in terms of a Git commit message.
This is a free text piece of metadata you can post on every change.

So we can track changes to a file structure.
What kind of changes are there?
-->

---

### File structure

<br>

<div class="columns2">

<div style="display: flex;">

<style scoped>
pre {
   font-size: 22px;
}
</style>

```bash
$ tree
.
|
├── file1.txt
├── file2.txt
├── dir1
│   ├── dir2
│   │   ├── file3.txt
│   │   └── file4.txt
│   └── file5.txt
├── dir3
│    ├── file6.txt
│    ...
│    └── file12.txt
...
```

</div>

<!--
Let's start with some terminology.
During this talk, I will use the word file structure to refer to
a bunch of files within potentially nested directories.

So essentially it's a folder containing files on your filesystem.
-->

---

![bg right:42% 86%](assets/final.png)

### Which problem does version control (e.g., Git) solve?

<sup>[image source][1]</sup>

[1]: https://phdcomics.com/comics/archive_print.php?comicid=1531

<!--
Which problem does version control solve?

There is this nice visualization of a problem,
probably everyone who has written a bachelor's or master's thesis,
might have faced.

You start working on a file (hopefully not using MS Office like in the drawing),
you reach a reasonable state which seems to be the final one,
but it isn't.
You share a state with your collaborators / or supervisor,
your get back comments, you do changes, you exchange new versions of your work.
While waiting on the review, you might advance into a different direction.

This process might repeat and you end up with
several copies with slightly varying content.

This process easily get's confusing,
especially if you have more than once collaborator
or more than one route of changes to go (variants..).

For MS Office products, nowadays there are collaboration features in place.
If your working on text files, no matter whether it is
code, documentation, presentation, evaluation, visualization,
there is a class of software that helps you to keep the overview of all the changes.

This class of software is version control systems.
-->

---

### Typical workflow of computational science.

![bg right:50% 86%](assets/workflow_01.png)

<!--
If you're not completely with me,
when I try to motivate version control systems using proprietary / commercial formats, I understand.

Let's look at a typical workflow in the field of computational science.
Usually, we start with some kind of data.
This could be the output of an experient
or a numerical simulation.

We then do some analysis or further comuptation,
often based on scripting logic (here called Analysis) which itself makes use of some kind of library.
We might develop the library on our own as part of a codebase.
The output of the analysis represents our result,
which often is a visualization or data prepared to get visualized.

The details to not matter, but I think this general pattern is applicable to most of your projects.

But all of these parts, usually are dynamic, right?
We work on this project and therefore,
there might be changes to... which influence the result, ...

Keeping track of these changes, is what version control helps us to do.

Note: We might control the data and results directly,
or we might choose to reference large data or results
on a separate file storage, optimized for large data,
using references.
There are solutions for handling large data.
But that's a more advanced topic...
-->

---

### Typical workflow of computational science.

![bg right:50% 86%](assets/workflow_02.png)

---

### Typical workflow of computational science.

![bg right:50% 86%](assets/workflow_03.png)

---

### Typical workflow of computational science.

![bg right:50% 86%](assets/workflow_04.png)

---

### Typical workflow of computational science.

![bg right:50% 86%](assets/workflow_05.png)

---

### Which types of changes to a file structure are possible?

<br>

- Change the content of a file (`echo "..." >> file.md`, ...)
- Create a new file (`touch file.md`, `echo "..." > file.md`, ...)
- Delete a file (`rm file.md`)
- Rename / Move a file (`mv file.md file2.md`)

<!--
The kind of actions are actually limited.
Which is great.
We can ...
-->

---

### How do we use Git?

Sequences of terminal **commands**
or using a **graphical interface**, e.g., within VSCode.

<br>

<div class="columnsflex">
<div>

<!-- <style scoped>
section div {
   /* flex: 3; */
   color: red;
}
</style> -->

Passive

```properties
git status
git diff
git log
git blame
...
```

</div>
<div>

Active

```properties
git add
git commit
git push
git pull
git merge
git checkout
...
```

</div>
</div>

---

### Where does Git work? (`.git`)

<br>

<div class="columns2">
<div style="flex: 10;">

```properties
➜  git_basics_slides tree -a -L 1
.
├── assets
├── .git
├── .github
├── .gitignore
├── LICENSE
├── main.md
...
├── README.md
├── themes
└── .vscode
```

</div>
<div style="flex: 8;">

```properties
➜  .git tree -a -L 1
.
├── branches
├── COMMIT_EDITMSG
├── config
├── description
├── FETCH_HEAD
├── HEAD
├── hooks
...
├── objects
...
```

</div>
</div>

---

### When does Git work?

<br>

Only during command execution.

---

### Example: Project Directory

<br>

<div class="columns2">
<div>

Directory

```properties
➜  my_project tree
.
└── main.py

0 directories, 1 file

```

</div>
<div>

File: `main.py`

```python
# main.py

name = "bill"

print(name)

```

</div>
</div>

---

### Example: Project Directory -> Git Repository (Init, Status)

<br>

![alt text](assets/example_init_dir_01.gif)

---

### Example: Project Directory -> Git Repository (Add)

<br>

![alt text](assets/example_init_dir_02.gif)

---

### Example: Project Directory -> Git Repository (Commit)

<br>

![alt text](assets/example_init_dir_03.gif)

---

### Example: Project Directory -> Git Repository (Config)

<br>

![alt text](assets/example_init_dir_04.gif)

---

### Example: Project Directory -> Git Repository (Log)

<br>

![alt text](assets/example_init_dir_05.gif)

---

### Example: Change a file

<br>

<div class="columns2">
<div>

Old

```python
# main.py

name = "bill"

print(name)

```

</div>
<div>

New

```python
# main.py

name = "bob"

print(name)

```

</div>
</div>

---

### Example: Change file content (Status)

<br>

![alt text](assets/example_06.gif)

---

### Example: Change file content (Diff)

<br>

![alt text](assets/example_07.gif)

---

### Example: Change file content (Status)

<br>

![alt text](assets/example_06.gif)

---

### Example: Change file content (Add)

<br>

![alt text](assets/example_08.gif)

---

### Example: Change file content (Commit, Status)

<br>

![alt text](assets/example_09.gif)

---

### Example: Change file content (Log)

<br>

![alt text](assets/example_10.gif)

---

### Git stages

![bg right:73% 90%](./assets/stages_01.png)

<sup>[image source][2]</sup>

[2]: https://medium.com/@zjpjack/reverting-modified-in-4-stages-in-git-f3997f526902

---

### Git stages

![bg right:73% 90%](./assets/stages_02.png)

<sup>[image source][2]</sup>

---

### Git stages

![bg right:73% 90%](./assets/stages_03.png)

<sup>[image source][2]</sup>

---

### Remote

![bg right:73% 90%](./assets/remote_01.png)

<sup>[image source][3]</sup>

[3]: https://www.zentao.pm/share/git-sync-remote-repos-update-179.html

---

### Remote

![bg right:73% 90%](./assets/remote_02.png)

<sup>[image source][3]</sup>

---

### Remote

![bg right:73% 90%](./assets/remote_03.png)

<sup>[image source][3]</sup>

---

### [Protocols](https://git-scm.com/book/ms/v2/Git-on-the-Server-The-Protocols)

<style scoped>
.temporaryDiv {
   font-size: 22px;
}
</style>

<div class="temporaryDiv">

- HTTP
- SSH

[See also Github authentication](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)

</div>

![bg right:70% 80%](./assets/github_clone_screen.png)

---

### Conflicts

<div class="columns3">

<style scoped>
section {
   font-size: 24px;
}
pre {
   font-size: 20px;
}
</style>

<div>

Left

```python
# main.py

name = "Lui"

print(name)

```

</div>
<div>

Old

```python
# main.py

name = "bill"

print(name)

```

</div>
<div>

Right

```python
# main.py

name = "Randell"

print(name)

```

</div>
</div>

**Manually resolve the conflict**: Tell Git whether to use

- the left change
- the right change
- a combination of both
- something completely new.

[**Merge Tools**](https://stackoverflow.com/questions/137102/whats-the-best-visual-merge-tool-for-git)

<!-- Git has powerful algorithm to combine changes from multiple authors.
However, sometimes people do conflicting changes, e.g., -->

---

### Branches

<br>

<!-- prettier-ignore-start -->


* Develop multiple features
* Develop different variantes
* **Make a proposal**


<!-- prettier-ignore-end -->

<sup>[image source][5]</sup>

[5]: https://stackoverflow.com/a/63253135/8935243

![bg right:40% 70%](./assets/branches.png)

---

### Log "A Dog"

<br>

![bg right:60% 50%](./assets/adog.png)

<sup>[image source][4]</sup>

[4]: https://stackoverflow.com/a/35075021/8935243

---

### Customized Log

<br>

```properties
➜  project git:(branch) git log --all --decorate --oneline --graph

| * 1554055 (origin/feedback_on_using_postprocessor, feedback_on_using_postprocessor) Tune comments and remove obvious explanatory ones
| * e5fdce1 Update project/postprocessors.py
| * 119036c Fix test after changes to signature
| * 7b6291f Playing with the postprocessor
|/
*   8a4c3d5 (main) Merge pull request #85 from project/postprocessing
|\
| * 2d48c0d fix index
| * 58c57e7 include hamiltonian to test
| * b30bba3 no need to use tikzexport by plotly, use csv directly and tweak in .tex
| *   ba3199d Merge pull request #84 from project/main
| |\
| |/
|/|
* | 84fbb66 correct reference results after bugfix
* | f5b32ea small bug fix
* | e45a266 small bug fixes and residual clean ups
* |   b6275ac Merge pull request #82 from project/discrete_gradient_methods
|\ \
| * | 7884cad abbreviate
| * | a8479a7 avoid overwriting reference solutions
| * | 9bd7ddf refactor DG part II
| * | ab42fb2 refactor discrete gradient
| * | 2210f40 refactor postprocessing
```

---

### Git Config and global `.gitignore`

<style scoped>
pre {
   font-size: 26px;
}
</style>

<br>

<div class="columns2">

<div>

[Show config](https://stackoverflow.com/a/12254105/8935243)

```
git config --list --show-origin

file:/home/julian/.gitconfig    init.defaultbranch=main
file:/home/julian/.gitconfig    core.editor=vim
file:/home/julian/.gitconfig    core.excludesfile=~/.gitignore
file:.git/config        core.repositoryformatversion=0
file:.git/config        core.filemode=true
file:.git/config        core.bare=false
file:.git/config        core.logallrefupdates=true
file:.git/config        user.name=julian
file:.git/config        user.email=julian@blub.com
(END)
```

</div>

<div>

[Global `.gitignore`](https://stackoverflow.com/questions/7335420/global-git-ignore)
(e.g. `.venv`, `.DS_Store`, ...)

<!-- - Create file `touch ~/.gitignore`
- Configure `git config --global core.excludesFile '~/.gitignore'`
- Lookup `git config --get core.excludesfile` -->

```
➜  touch ~/.gitignore

➜  git config --global core.excludesFile '~/.gitignore'

➜  git config --get core.excludesfile
~/.gitignore
```

</div>
</div>

---

### [Git Large File Storage (LFS)](https://git-lfs.com/)

- Keep repos small
- Work like you always do

![bg right:60% 75%](assets/git_lfs.gif)

---

### Summary

<br>

- The Git way of working: Change, add, commit, pull, push, repeat
- Applications:
  - Code
  - Latex
  - Any computational project

---

### Outlook

- Git in your integrated development environment (IDE)
- Hooks, e.g., `pre-commit`
- Github / Gitlab
- Continuos integration (CI) with Github Actions / Gitlab CI/CD
- Git large file storage (LFS) at your university
- [Git workflows][git_workflows_atlassian]: Centralized, feature branching, gitflow workflows, forking workflow

[git_workflows_atlassian]: https://www.atlassian.com/git/tutorials/comparing-workflows

---

### Resources

- [Software Carpentry: Git-Novice](https://swcarpentry.github.io/git-novice/)
- [Git for beginners: The definitive practical guide](https://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide)
- [The Git docs](https://git-scm.com/doc)
