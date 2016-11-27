# Set up a new project

You can set up a new project based on [angular-seed](https://github.com/robstoll/angular-seed) as follows:

```bash
# clone the angular-seed into a directory called yourProjectName (get only last commit, not the whole history)
git clone --depth 1 https://github.com/robstoll/angular-seed yourProjectName
cd yourProjectName

# exchange the remote called origin with your remote repository
git remote remove origin
git remote add origin https://github.com/yourName/yourProjectName

# we are using a branch called seed-last-update and a remote called 'seed' to keep track on which commit 
# (of angular-seed) this project is based on in order to get updates of angular-seed later on
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

open [README.md](README.md) in your favourite editor and work through the TODOs.

# Apply angular-seed Updates
If you want to apply an update (one or several commits) of [angular-seed](https://github.com/robstoll/angular-seed) 
to your project then you can proceed as follows:

```bash
# get the latest version of the seed
git fetch seed

# squash all commits from seed/master which were made since seed-last-update into one commit 
# and merge it into a new branch called seed-update-commit 
git checkout -b seed-update-commit seed-last-update
git merge --squash seed/master

# Commit the changes -- you might want to replace the title with the following
# Squashed last changes from robstoll/angular-seed
git commit 

# cherry-pick the commit into master
git checkout master
git cherry-pick seed-update-commit
git push

# move the seed-last-update branch forward
git checkout seed-last-update
git reset --hard seed/master
git push

# delete the seed-update-commit branch 
git branch -D seed-update-commit
git checkout master
```

# Contributing to angular-seed

We appreciate that you want to contribute to angular-seed by either report bugs, suggest a new feature or a pull request.
Please see the [CONTRIBUTING](https://github.com/robstoll/angular-seed/blob/master/.github/CONTRIBUTING.md) file for guidelines.
