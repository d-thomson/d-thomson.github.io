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

Once you have a repository created, locally speaking, you have three trees that are maintained by git. The first is the working directory. This holds your actual files on your system. The second is the index or staging area. This is what will house your local changes. The third is HEAD, this will point to the last commit that you have made.

The typical workflow is illustrated below:

![](../img/git_workflow.png?raw=true "Typical git workflow")

The intermediary commands for moving data are described in further detail next, but knowing these distinct locations are crucial to understanding git. 

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

If you want to tag a specific commit hash, you can do so by appending the hash to the tag command.
```
git tag v1.0 76de721cfe92b081e2508224c21b3ed6e107e148
```

#### Recovery
In case you messed up a file and want to start fresh, you can replace local changes for that file using the checkout command. This will replace any changes in your working directory with the content in HEAD. Any changes that are added to your index will be kept, however you can remove these by using the reset command.
```
git checkout -- myfile.rb
```

If your local repository is destroyed to the point of no return, there is a way you can drop all local changes and commits. First you need to use the fetch command followed by the reset command. The following will point your local master branch to the latest history from the remote repository.
```
git fetch origin
git reset --hard origin/master
```

#### References
Above was a quick overview of git. The full reference guide can be found here.

[git Documentation](https://git-scm.com/docs)

## Example

This section contains a worked example to help get you better acquainted with git.

#### Setup
If you haven't already, [download and install git](https://git-scm.com/downloads) then [create an account](https://github.com/join) on Github.com, create an empty repository named `git-tutorial`.

#### Part I
In this section we will get the feel of working with the basic git workflow. Try to complete the following tasks from a terminal window. If you get stuck, try using the tutorial as a reference before jumping to the solution.

1. Open a terminal window.
2. Create and go to directory `my-dir`.
3. Clone the empty repo you created in setup with a custom name `my-repo`.
4. Go to `my-repo`.
5. Create a file named `readme.md` and add the line "git is easy!" to the file.
6. Commit the file to your local repo with the message "Added readme"
7. Create a new branch named `dev` and switch to it.
8. Create a new file named `my_file.rb` with the content "puts 'Hello, world!'".
9. Commit the file (should be to the `dev` branch) with the message `Added my_file.rb`.
10. Switch to the `master` branch
11. Add another line (below `git is easy`) to the `readme.md` file, "sort of easy..."
12. Commit the change to your local repo with the message `Changes to readme`
13. Merge the `dev` branch to the `master` branch with the message "Merging dev to master"
14. Tag the last commit in the log with "v1.0".
15. Push all branches to the remote repository.

~~~
# 2
mkdir my-dir
cd my-dir

# 3, 4
git clone https://github.com/d-thomson/git-tutorial.git my-repo
cd my-repo

# 5, 6
touch readme.md
echo git is easy! >> readme.md
git add readme.md
git commit -m "Added readme"

# 7, 8
git checkout -b dev
touch my_file.rb
echo puts 'Hello, world!' >> my_file.rb

# 9
git add my_file.rb
git commit -m "my_file.rb"

# 10, 11
git checkout master
echo sort of easy... >> readme.md

# 12
git add readme.md
git commit -m "Changes to readme"

# 13
git merge dev -m "Merging dev to master"

# 14
git log -1
git tag v1.0 <hash>

# 15
git push origin dev
git push
~~~

#### Part II
In this section, we will open another terminal window to simulate another user making changes to your repository. Each terminal window will simulate a user. Here we will handle a merge conflict. Again, if you get stuck, try using the tutorial as a reference before jumping to the solution.

1. Open a second terminal window.
2. Create and go to directory `my-dir-2`.
3. Clone the repo from part I with the custom name `my-repo`.
4. Switch to the `dev` branch.
5. Create a file named `my_file_2.rb` with the text `puts 'more ruby files!'`.
6. Commit the file to your local repo (in the `dev` branch) with the message "Added more ruby files"
7. Switch to the `master` branch
8. Merge the `dev` branch to the `master` branch with the message "Merging dev to master, again"
9. Add another line (below `sort of easy...`) to the `readme.md` file, "nobody is using this, right?"
10. Commit the file to your local repo (in the `master` branch) with the message "Changes to readme.md"
11. Push all branches to the remote repository.

At this point, switch back to your initial terminal.

12. Switch to the `master` branch (if not already in it)
13. Add another line (below `sort of easy...`) to the `readme.md` file, "I'm using this!"
14. Commit the file to your local repo with the message "Changes to readme.md"
15. Push the master branch to the remote repository.

At this point, you will need to handle the conflict in readme.md. Do not lose any content and remove all text that was added by git to mark the conflicting pieces. Once the conflict was resolved:

16. Commit the resolved conflict with the message "Final merge with conflicts fixed".
17. Push all branches to the remote repository.

~~~
# 2
mkdir my-dir-2
cd my-dir-2

# 3, 4
git clone https://github.com/d-thomson/git-tutorial.git my-repo
cd my-repo

# 4, 5
git checkout dev
touch my_file_2.rb
echo puts 'more ruby files!' >> my_file_2.rb

# 6
git add my_file_2.rb
git commit -m "Added more ruby files"

# 7, 8
git checkout master
git merge dev -m "Merging dev to master, again"

# 9, 10
echo nobody is using this, right? >> readme.md
git add readme.md
git commit -m "Changes to readme.md"

# 11
git push origin dev
git push

# 12, 13 (Now in terminal one)
git checkout master
echo I'm using this! >> readme.md

# 14, 15
git add readme.md
git commit -m "Changes to readme.md"
git push

# resolve the conflict in the file. Remove any git text and leave the 4 lines.

# 16
git add readme.md
git commit -m "Final merge with conflicts fixed"

# 17
git push
~~~

## Tips, Tricks and Interview Questions

#### Useful Tips & Tricks
Git comes with a built-in GUI. It can be launched from the terminal wiht the following command. This is very helpful for visualizing branching and viewing the changes within files. It's also great for dealing with merge conflicts.
~~~
gitk
~~~

Syntax highlighting for git output is helpful, and let's be honest it looks pretty.
~~~
git config color.ui true
~~~

It's often useful to show the log on one line per commit, in case you want to tag or share the hash with a coworker. To do so we can set this in the git config.
~~~
git config format.pretty oneline
~~~

You can see the changes to all files in the working tree, changes to a specific file or the changes between the working directory and staging by using the `git diff` command.
~~~
git diff
git diff <path_to_file>
git diff --staged
~~~

#### Common Interview Questions

- **What is a conflict in git**

A conflict in git arises when a merge between branches have differing changes on the same line of a file. They can also occur when one branch contains a file deletion however changes are made in the other branch.The auto-merge will fail since precendence cannot be determined.

- **How are conflicts resolved?**

The user will need to resolve git conflicts manually before merging branches. First, they must edit the files to fix the conflicting changes. Next, they will need to add the resolved files to their index by running `git add` and finally committing the repaired merge using `git commit`.

- **What is git stash?**

The stash command takes the current state of your working directory and index, and places them on a stack. The working directory is cleaned and your edits are stashed for later. This will revert you to the HEAD commit, you can view your stash stack with `list`, drop stack entries with `drop` and even checkout stashed entries to a new branch with `branch`.

- **What is the difference between git pull and git fetch?**

The fetch command will pull all new commits from the desired branch and store them in a new branch in your local repository. To update your local repository with these changes, you will need to merge the fetched branch with the target branch. The git pull command does these operations simultaneously, the pull command will always attempt to auto-merge your target branch with the most recent commit.

- **What does git config do?**

The config command allows you to set options for your git installation. Repository behavior, user and authentication information, and preferences can all be set through this command.
