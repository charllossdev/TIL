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

#### Initializing a Repository in an Existing Directory

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


### Step.3

```Git
$ git remote add origin "Github Repository URL"

```

```Git
$ git push origin master
```

---

# ERROR

```
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/charllossDev/TIL.git'
```

"git merge" used to allow merging two branches that have no common base by default, which led to a brand new history of an existing project created and then get pulled by an unsuspecting maintainer, which allowed an unnecessary parallel history merged into the existing project. The command has been taught not to allow this by default, with an escape hatch "--allow-unrelated-histories" option to be used in a rare event that merges histories of two projects that started their lives independently.


현상
github에서 저장소 생성 후 저장소 주소를 remote에 입력(git remote add origin https://github…..)했고, 로컬에서도 정상적으로 초기화(git init)했는데도 git pull 또는 git merge 명령이 동작하지 않고 git push origin master시 [rejected] master -> master (non-fast-forward)이런 에러가 발생하는 경우

원인
깃허브에 생성된 원격 저장소와 로컬에 생성된 저장소 간 공통분모가 없는 상태에서 병합하려는 시도로 인해 발생. 기본적으로 관련 없는 두 저장소를 병합하는 것은 안되도록 설정되어 있음.

해결방법
아래와 같이 git pull 시에 –allow-unrelated-histories 옵션 추가하여 관련 없었던 두 저장소를 병합하도록 허용

git pull origin master --allow-unrelated-histories
