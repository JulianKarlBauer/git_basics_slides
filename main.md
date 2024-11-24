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
# footer:
---

# Commit to Git?

#### A short introduction to version control in computational sciences

<br>
<br>

04.12.2024
Julian Karl Bauer

<!--
Thank you for introduction
Thanks for inviting

I really liked Emils presentation
'...' .
An important building block for all the things Emil had talked about is version control.
This gave me motivation to kind of recycle a talk on Git basics I gave some years ago.
Probabyl the world changed and all of you have a profound understaning of which version control is and how to use it.
But I was encouraged, that recaping the basics, might be a thing worth doing.
That's why, I would like to give a very rough introduction to basic concepts of version control, focussing on Git.
-->

---

<!-- _class: outline -->

### Outline (Just for development of these slides)

- What is Git?
- Which problem does Git solve?
- File structure
- Actions on a file structure
- Motivation workflow
- FINAL.doc
- What is it like to work with Git?
- Where does Git store all the information?
- Example: Change a file
- Git stages
- Remote
- Sequential / Parallel?
- Conflicts
- Branching
- How to ignore specific files?
- Do you really use a terminal?

---

### What is Git?

<br>

<!-- prettier-ignore-start -->

* Command line interface (CLI)
* A distributed version control system
* The second big project of Linus Torvald
* A [content-addressable filesystem][git_internals]

<!-- prettier-ignore-end -->

[git_internals]: https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

<!--

Let's start with a simple question: What is Git?

There are certainly a number of legitimate answers...
For example:
- ...

-->

---

### Which problem does Git solve?

![bg right:40% 80%](assets/final.png)

---

### Which problem does Git solve?

<br>

**Track changes** to a **file structure** including **metadata** on

- Who: Author
- When: Timestamp
- Why: Elaboration in commit message

and **enable structured collaboration** among team members.

---

# Multi columns in Marp slide

<div class="columns">
<div>

#### Column 1

Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptas eveniet,

</div>
<div>

#### Column 2

Tempore ad exercitationem necessitatibus nulla, optio distinctio illo non

</div>
</div>

---

![bg opacity](./assets/gradient.jpg)

# First slide

Vanilly text

https://wikipedia.de

<style scoped>a { color: #36c; }</style>

<!-- This is presenter note. You can write down notes through HTML comment. -->

---

```python
a = 10
```

---

# Pure image slide

![Marp bg 60%](https://raw.githubusercontent.com/marp-team/marp/master/marp.png)

---

<!-- _backgroundColor: "#123" -->
<!-- _color: "#fff" -->

# <!--fit--> Some fitting sub heading

##### <!--fit--> Another fitting sub heading

#### 4. heading Not fitting

###### 6. heading Not fitting

---

# New slide

## Subheading on new slide

nested button with hyperlink and specified size:

[![Deploy to Vercel h:1.5em](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/yhatt/marp-cli-example)
