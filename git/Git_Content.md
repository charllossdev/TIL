# Git Content

# Categories

0. [What is Git?](#what-is-git?)
0. [Git Command](#git-command)


---

# What is Git?

[What is Git: Bitbucket](!https://www.atlassian.com/git/tutorials/what-is-git)

Git is a **distributed version control[^1]** system for tracking changes in source code during software development.

It is designed for coordinating work among programmers, but it can be used to track changes in any set of files.

Its goals include speed, data integrity, and support for distributed, non-linear work flows.


[^1]: In software development, distributed version control is a form of version control where the complete code base - including is full history - is mirrored on every developer's computer. This allows branching and merging to be managed automatically, increases speeds of most operations.


# Git Command

## Getting Started

> First-Time Git Setup

Now that you have git on your system, you'll want to do a few things to customize your git environment.
You should have to do these things only once on any given computer.
They'll stick around between upgrades.
You can also change them at any time by running through the commands again.

### Step.1 Identity

The first thing you should do when you install Git is to set your user name and email address.
This is important because every Git commit uses this information, and it's immutably baked into the commits you start creating

```Git
$ git config --global user.name "Your Git Nmae"
$ git config --global user.email "Your Git Email"
```

### Step.1.1 All Checking Your Settings

If you want to check your configuration settings, you can use the *git config --list* command to list all the settings Git can find at that point.

```Git
$ git config --list
```

or You can also check what git thinks a specific key's value is by typing *git config <key>*

> Check Your specific key Configure Setting

```Git
$ git config user.name
$ git config user.email
```

### Step.2  Getting a Git Repository

**Initializing a Repository in an Existing Directory**

If you have a project directory that is currently not under version control and you want to start controlling it with Git, you first need to go to that project's directory.
If you've never done this, it looks a little different depending on which system you're running.

```Git
$ git init
```

This create a new subdirectory named .git that contains all of your necessary repository files -- a Git repository skeleton.
At this point, noting in your project is tracked yet.

Next If you want to start version-controlling existing files (as opposed to an empty directory), you should probably begin tracking those files and do an initial commit.
You can accomplish that with a few git add commands that specify the files you want to track, followed by a git commits

```Git
$ git add files or directory

$ git commit -m "Message"
```


> Message Tips!
>> First Title Keywords

* feat
* fix
* docs
* style
* refactor
* test
* chore
