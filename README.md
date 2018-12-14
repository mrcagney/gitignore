# .gitignore for MRCagney

The purpose of this repo is to provide some easily downloadable custom .gitignore files for a project. There are two types of .gitignore files:

  1. Global, and
  2. Local.

A global .gitignore is one which is a user specific .gitignore used in every git repo on their machine. For example, max OSX files have a hidden .DS_Store journal file in folders.

A local .gitignore is one which is used in specific project e.g. for a python or R project. In R, you'd want to exclude your personal project file (\*.RProj) and history file (.RHistory).

## Setting up a global .gitignore

Simply download the file and run the following command at the terminal / command promot substiting the name of the file you wish to be your global file.

    git config --global core.excludesfile ~/.put_your_global_gitignore_here

## Setting up a local .gitignore

To set up a local file, you need to create bash / command prompt script to:

  1. initialise a git repo,
  2. accept a .gitignore file specification e.g. Python,
  3. downland and place in the git init repo.

The following bash script should work on Linux and MacOSX:

    #!/bin/sh

    git init .
    curl -o .gitignore --fail --show-error --silent --location https://raw.github.com/github/gitignore/master/$1.gitignore
    git add .gitignore && git commit -m "added gitignore from GitHub"
