# Source Control

## Introduction

Source or version control is the practice of tracking and managing changes to code. Source Control Management (SCM) systems provide a running history of code development and help to resolve conflicts when merging contributions from multiple sources. When working on a project with multiple team members, version control is imperitive to success.

Git is an open-source distributed source code management system. Git allows you to create a copy of your repository known as a branch. Using this branch, you can then work on your code independently from the stable version of your codebase. Once you are ready with your changes, you can store them as a set of differences, known as a commit. You can pull in commits from other contributors to your repository, push your commits to others, and merge your commits back into the main version of the repository.

## Tutorial

Below is a short tutorial on the Git source control management system. Git is considered a standard in source control.

#### Setup

The first thing you must do before using Git is download and install it. Installers for OSX, Windows and Linux can be found in the link below.

[Download git](https://git-scm.com/downloads)

Once installed and configured for your architecture, you can confirm the install by entering the following command.
~~~
git --version
~~~

This will print the version to the console. If you do not see the version number, you may need to manually add git's bin directory to your PATH environment variable. You will also have to tell git who you are for authentication purposes. First, you shuld create a github account, since you will need this to work through the example.

[Join Github](https://github.com/join)

~~~
git config --global user.name "Jane Doe"
git config --global user.email jdoe44@gatech.edu
~~~

#### New Repository

To create a new respoitory, create or open a directory and perform 
~~~
git init
~~~

This will create a new local repository for that folder. You can also checkout or `clone` a repository from a local directory, remote server or website. You can also specifiy a name other than that of the repo by adding an optional string parameter after the clone operation. Below we give the name `my-sample-repo` to the `6460-sample-repo` respoitory.

~~~
git clone /path/to/the/repo`
git clone user@host:/path/to/the/repo`
git clone https://github.com/d-thomson/6460-sample-repo.git my-sample-repo`
~~~

Once you have cloned a repository, you will notice that the end of the directory now has `master` associated with it.

#### Workflow

Your local repository consists of three "trees" maintained by git. the first one is your Working Directory which holds the actual files. the second one is the Index which acts as a staging area and finally the HEAD which points to the last commit you've made.


#### Staging

To add files to your index, where you will be proposing your changes, you can use the add command.
~~~
git add myfile.rb
~~~

You can also add any files in bulk that contain changes between your working directory and HEAD. To add all use the `*` modifier. You can add entire subdirectories by specifying a path.
~~~
git add *
git add path/to/dir/*
~~~

If you need to remove some files from your index, you can use the reset command.
~~~
git reset myfile.rb
~~~

#### Commit & Push
Once you have proposed changes in your index, you can commit these files to HEAD. Commits [require a message](https://xkcd.com/1296/), you can add one using a text editor or by using the `-m` flag to specify your message in the commit command.
~~~
git commit -m "Committing some changes..."
~~~

Now that we've committed some files to HEAD, our local working copy, we can send these changes to the remote repository using the `push` command.
~~~
git push
~~~

#### Branching

Branches are used to develop features that are isolated from each other. By default, the master branch is the initial head where you created your repository. You can use other branches to develop features then merge them back into an upstream branch once completed.
 
We can create a new branch by using the checkout command. Checkout allows us to switch  between branches in our local repository or create new ones. To create a new branch, use checkout with the -b flag.
~~~
git checkout -b mybranch
~~~

Branches also stay local to you unless you specifically push the branch to your remote repository
~~~
git push origin mybranch
~~~

If we want to switch back to the master branch, we just need to specify the name of the branch in the checkout command. 
~~~ 
git checkout master
~~~


#### Update & Merge
To update your working copy to the latest commit, we can use the `pull` command. This pulls down any changes that have been made to the remote repo since your last pull.
~~~
git pull
~~~

Git will always attempt to auto-merge whenever you pull, however, sometimes this doesn't meld well. Multiple users could be modifying a file and overwriting the same lines that you have in your local copy causing conflicts.
```
git merge mybranch
```

You will have to manually resolve any conflicts in each file and confirm they are merged by adding them to your index. 
```
git add myfile.rb
```

A useful command for dealing with merges is to use the git diff feature between two branches.
```
git diff mybranch anotherbranch
```
 
#### Tags & Log
It is common practice to tag your versions for release. You can create a new tag, for example v1.0, using the tag command.
```
git tag v1.0
```

To view a repositories history, you can use the log command. This will print every commit, you can specify to only print a persons commits or even just grab the latest commit id, or a combination of both.
```
git log
git log -1
git log --author=jdoe44@gatech.edu
git log -1 --author="Jane Doe"
```

#### Recovery
In case you did something wrong, which for sure never happens ;), you can replace local changes using the command
git checkout -- <filename>
this replaces the changes in your working tree with the last content in HEAD. Changes already added to the index, as well as new files, will be kept.

If you instead want to drop all your local changes and commits, fetch the latest history from the server and point your local master branch at it like this
git fetch origin
git reset --hard origin/master

#### Reference
Above was a quick overview of git. The full reference guide can be found here.

[git Documentation](https://git-scm.com/docs)

## Example

This section contains a worked example to get you more acquainted with git.

Create a new folder, and initialize a repository.
<details>
<summary>Solution</summary><p>
 
~~~
mkdir git-tutorial
cd git-tutorial
git init
~~~
</p></details>
   

## Tips, Tricks and Interview Questions

Here are some tips, tricks and common interview questions.
