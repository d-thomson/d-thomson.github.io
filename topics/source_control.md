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

This will print the version to the console. If you do not see the version number, you may need to manually add git's bin directory to your PATH environment variable.

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


## Example

Here is a worked example.

## Tips, Tricks and Interview Questions

Here are some tips, tricks and common interview questions.
