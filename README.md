# .gitignore for MRCagney

The purpose of this repo is to provide some easily downloadable custom .gitignore files for a project. There are two types of .gitignore files:

  1. global, and
  2. local.

A global .gitignore is one which is a user specific .gitignore used in every git repo on their machine. For example, MacOSX files have a hidden .DS_Store journal file in folders.

A local .gitignore is one which is used in specific project e.g. for a python or R project. In R, you'd want to exclude your personal project file (\*.RProj) and history file (.RHistory).

## Setting up a global .gitignore

Simply download the file and run the following command at the terminal / command prompt substituting the name of the file you wish to be your global file:

    curl -o .global.gitignore --location https://raw.github.com/phildonovan/gitignore/master/globals/macOS.gitignore
    git config --global core.excludesfile ~/.global.gitignore

## Setting up a local .gitignore

To set up a local file, you need to create bash / command prompt script to:

  1. initialise a git repo,
  2. accept a .gitignore file specification e.g. Python,
  3. downland and place in the git init repo.

The following bash script should work on Linux and MacOSX:

    #!/bin/sh

    git init .
    curl -o .gitignore --fail --show-error --silent --location https://raw.github.com/phildonovan/gitignore/master/$1.gitignore
    git add .gitignore && git commit -m "Added .gitignore from MRCagney Gitlab"

Call the script git-init-more.sh, chmod +x it, and put it in your path, then you can invoke it like this:

    git init-more R

Remember to use capitals for the name of the file if it has them.

## To do

  * Figure out how to do this on a Windows machine. (use linux or mac!)
  * Alex add linux global and update with your .gitignore files you like to use.
