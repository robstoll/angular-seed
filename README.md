# Introduction

[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)
[![Build Status](https://travis-ci.org/robstoll/angular-seed.svg?branch=master)](https://travis-ci.org/robstoll/angular-seed)
[![Build Status](https://ci.appveyor.com/api/projects/status/github/robstoll/angular-seed?svg=true)](https://ci.appveyor.com/project/robstoll/angular-seed)
[![Dependency Status](https://david-dm.org/robstoll/angular-seed.svg)](https://david-dm.org/robstoll/angular-seed)
[![devDependency Status](https://david-dm.org/robstoll/angular-seed/dev-status.svg)](https://david-dm.org/robstoll/angular-seed?type=dev)

This is a seed project for angular based projects. It is itself based on [mgechev's angular-seed](https://github.com/mgechev/angular-seed/).

**TODO, complete the following steps**

1. Setup up the project as described in the section (installation below)
1. Delete the text above and write your own introduction 
2. Update the links of the badges above (to reflect your repository)
3. Update LICENSE file (and section 'License' below)
4. Update package.json file (name, version, description, author ...)
5. Modify .travis.yml (or remove it if you do not use travis)
    1. Change the path in after_failure so it reflects your repository
    2. Uncomment the part about gitter in the notifications section and adjust the url in case you use gitter
6. Modify appveyor.yml (or remove it if you do not use appveyor)
    1. Uncomment the notifications section and adjust the gitter url in case you use gitter


# Installation

You can set up a new project with the seed as follows

```bash
# clone the angular-seed into directory called yourProjectName (get only last commit, not the whole history)
git clone --depth 1 https://github.com/robstoll/angular-seed yourProjectName
cd yourProjectName

# exchange the origin with your remote repository
git remote remove origin
git remote add origin https://github.com/yourName/yourProjectName

# we are using a branch called seed-last-update and a remote called 'seed' to keep track on which commit 
# (of angular-seed) this project is based on in order to perform updates of angular-seed later on
git checkout -b seed-last-update
git remote add --no-tags --track master seed https://github.com/robstoll/angular-seed
git fetch seed --unshallow
git push -u origin seed-last-update

# since master should not have a parent we delete it and re-create it as orphan branch
git branch -d master
git checkout --orphan master

# make your first commit and push to orign (set up master tracking origin/master)
git commit -m "initial commit based on robstoll's angular-seed"
git push -u origin master
```

install the node_modules

```bash
# either install the project's dependencies with yarn (via Yarn, https://yarnpkg.com)
yarn install  
# or with npm (which is most probably slower)
npm install
```


# Apply Updates
If you want to apply an update (one or several commits) of angular-seed to yourProjectName then you can proceed as follows:

```bash
# get the latest version 
git fetch seed
# have a look at what has been changed since your last update (copy the first and last commit hash)
git log ..seed/master

# merge all changes into a new branch and squash it to one commit 
git checkout seed-last-update
git checkout -b seed-update-commit
git merge --squash seed/master

# Commit the changes and replace lastCommitHash and firstCommitHash with the actual hashes 
$ git commit -m "Merge robstoll/angular-seed/master
> Squashed commits starting from lastCommitHash to firstCommitHash"

# move the seed-last-update branch forward
git checkout seed-last-update
git reset --hard seed/master
git push

# cherry-pick the commit into master
git checkout master
git cherry-pick seed-update-commit
git push

# delete the seed-update-commit branch 
git branch -D seed-update-commit
```


# Contributing

Please see the [CONTRIBUTING](.github/CONTRIBUTING.md) file for guidelines.


# Based on robstoll's angular2-seed

This project is/was using [robstoll's angular-seed](https://github.com/robstoll/angular-seed) --
which in turn is based on [mgechev's angular-seed](https://github.com/mgechev/angular-seed/) -- to start off.

Please refer to mgechev's repository for further details and help. 


# License

Work is licensed under: [MIT](LICENSE)  
Seed is licensed under: [MIT](LICENSE-seed)
