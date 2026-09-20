# asen4018-green-fsw
This repository houses all flight software for the ASEN Capstone Green team for the astrodynamics/remote sensing section. 

# 1. Getting Started

## 1.1 Cloning the Repository for Development

## 1.2 Cloning the Repository onto Flight Module

## 1.3 Workflow 

### 1.3.1 Some Helpful Aliases
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

> Note: On Linux (sorry Windows), you can also configure terminal to autocomplete by adding `export GIT_COMPLETION_CHECKOUT_NO_GUESS=1` to `~/.bashrc` and running `source ~/.bashrc`.

### 1.3.2 Manifests and Versioning

### 1.3.3 Tags
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


# 2. Setting up the Flight Software

## 2.1 System Setup

## 2.2 Flight Software Compilation
