# asen4018-green-fsw
This repository houses all flight software for the ASEN Capstone Green team for the astrodynamics/remote sensing section. 

# 1. Getting Started

## 1.1 Cloning the Repository for Development

## 1.2 Cloning the Repository onto Flight Module

## 1.3 Workflow 
Example tag 
```bash
# in asen4018-green-fsw
git checkout stable
git merge dev
git tag -a v1.0.0-alpha -m "Stable flight loop code"
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

### 1.3.1 Manifests

### 1.3.2 Tags


# 2. Setting up the Flight Software

## 2.1 System Setup

## 2.2 Flight Software Compilation
