# asen4018-green-fsw
This repository houses all flight software for the ASEN Capstone Green team for the astrodynamics/remote sensing section.

# 1. Repository Quickstart
This section provides the quick instructions for getting started with flight code development/checkout. If you need a particular setup or will be doing more in depth work, we recommend following the more detailed instructions in [repo-setup.md](docs/repo-setup/repo-setup.md). 

## 1.1 F Prime Environment Setup

## 1.2 Cloning the Repo for Development
On the [homepage](https://github.com/ASEN-Capstone-Green/asen4018-green-fsw) of the repository, scroll up to the top of the page and click the Green `<> Code ▾` button. Use your preferred cloning method (SSH, HTTPS, CLI) to clone the repository to your local machine. E.g. if you wanted to use SSH, you would run the following at the local file location you want to clone the repository to:
```shell
git clone git@github.com:ASEN-Capstone-Green/asen4018-green-fsw.git
```

From there, navigate to the project root and switch to `dev` with:
```shell
git checkout dev
```

Then you can start on development by checking out your own new feature branch with:
```shell
git pull # makes sure your dev branch is up to date
git checkout -b feature/your-new-feature # creates and switche to the new branch
git push -u origin HEAD # pushes your local branch to remote
```

Finally, once you have code ready for testing on hardware (i.e. compiled and working on your local F Prime instance), push your code to remote and create a pull request for your branch to dev (make sure to merge dev into your branch if it has been updated!) at [the pull requests page](https://github.com/ASEN-Capstone-Green/asen4018-green-fsw/compare) and reach out to Luke or your subsystem lead. 

## 1.3 Flashing FSW onto the Flight Module


# 2. Workflow

## 2.1 Manifests and Versioning

## 2.2 Tags
<!--
Example tag
```shell
# in asen4018-green-fsw
git checkout stable
git merge dev
git tag -a v1.0.0-rc.4 -m "Stable flight loop code"
git push origin stable --tags
```

```shell
# in the ASEN4018_Green repository
cd flight-software
git checkout stable
git pull origin stable

cd ..
git add flight-software
git commit -m "Update FSW submodule to stable release v1.0.0-alpha"
git push origin main
```
-->

## 2.3 Some Helpful Aliases
Aliases basically allow you to define your own custom commands which bunder other commands, which can speed up the development process. For this repository, the useful alias configurations and an example of how they might be used are shown below:

```shell
# 1. new-feature
git config --local alias.new-feature '!git checkout dev && git pull && git fetch --prune && git checkout -b'
## ex:
git new-feature dev-1.4/gps-sensor

# 2. rm-feature (rm is short for remove)
git config --local alias.rm-feature '!git checkout dev && git pull && git fetch --prune && git branch -d'
## ex:
git rm-feature dev-1.4/gps-sensor

# more to come, soon(TM)
```

> Note: you can view all your active aliases with `git config --list`.

> Note: On Linux and WSL (sorry Mac users), you can also configure terminal to autocomplete by adding `export GIT_COMPLETION_CHECKOUT_NO_GUESS=1` to `~/.bashrc` and running `source ~/.bashrc`.
