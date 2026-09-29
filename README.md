# asen4018-green-fsw
This repository houses all flight software for the ASEN Capstone Green team for the astrodynamics/remote sensing section.

# 1. Repository Quickstart
This section provides the quick instructions for getting started with flight code development/checkout. If you need a particular setup or will be doing more in depth work, we recommend following the more detailed instructions in [repo-setup.md](docs/repo-setup/repo-setup.md). 

## 1.1. F Prime Environment Setup

### 1.1.1. System Requirements
Regardless of your system, you'll likely want to install [VSCode](https://code.visualstudio.com/download), it's a code editor and terminal app with a ton of integrations and support. You shouldn't need to do anything different than the default setup options for now.

Since F Prime (sometimes called F') natively runs on Unix based systems, Windows users will need to install Window Subsystem for Linux (WSL or WSL2). For Windows users, once you have completed the steps in [Section 1.1.2.](#112-windows-wsl-setup), you can continue on to [Section 1.1.3.](#113-linux-and-macos-setup)

For Linux and MacOS users, you can skip straight to [Section 1.1.3.](#113-linux-and-macos-setup)

### 1.1.2. Windows WSL Setup
Windows Subsystem for Linux essentially runs a mini version of Linux in your terminal. This means we can run and compile code without needing to install a full virtual machine with a GUI (would be a little slow, and a large download) or dual booting (running two operating systems on your PC, can get complicated). 

To install WSL:

1. Open a terminal (VSCode terminal (press ``<Ctrl+`>``), powershell, terminal, etc.).
2. Run the following:
```shell
wsl --install
```
3. You will need to restart your computer when prompted by the install. 

> By default, this will install Ubuntu (one of the more common Linux distributions, or OS releases). You can do a different version if you'd like, but for simplicity's sake, we're only including the default instructions here. 

4. A console should automatically open upon restart (you can also open any terminal and type `wsl` or open the Ubuntu app from the Start Menu).
5. Wait for the setup to finish compressing files.
6. Enter a Unix username and password when prompted. 
7. Update Linux by running the following:
```shell
sudo apt update && sudo apt upgrade -y
```

Once WSL is installed, we will want to set up git credentials **IN** WSL proper so that we can install the FSW repository in your Linux environment. We do this so that compilations don't cross the Windows-Linux interface, which would slow things down pretty noticably.

> This repository is public, so you don't need credentials to pull down code and start working on your local version. However if you ever want to push code from the command line, you'll need to set up git authentication, which I have [detailed instructions for here](https://github.com/bassett-luke/GitHub-Reference/blob/main/README.md#22-authentication).

Then, to install the VSCode WSL extension:
1. Open VSCode in windows (if it isn't already).
2. Click the extensions icon on the left sidebar (or press Ctrl+Shift+X).
3. Search for WSL (published by Microsoft) and click Install.

Then a couple last things:
1. The easiest way to open VSCode to terminal is pressing the button in the bottom left that looks like a `>` and a `<` put together and selecting "Connect to WSL" from the dropdown. 
    * After you do this once, you can then go to **File > Open Recent** and select the FSW repository from those options, and it will automatically open the repo in WSL. 
    * You can also open the Ubuntu app and type `code .` to open VSCode to your current directory. You may have to click Allow on a prompt.
2. You can set your default terminal profile in VSCode by going to **File > Preferences > Settings** (or pressing `<Ctrl+,>`) and searching `terminal.integrated.defaultProfile.windows`, then selecting WSL from the dropdown.

From this point forward, all documentation in the repository will assume you have this setup correctly, so instructions will likely not work in Windows PowerShell.

### 1.1.3. Linux and MacOS Setup
Once you have Linux, MacOS, or WSL setup, you will want [git](https://git-scm.com/install/), [CLang](https://clang.llvm.org/get_started.html) OR [Gnu Compiler Collection](https://gcc.gnu.org/install/), and [python 3.10+](https://www.python.org/downloads/). Most Linux distributions already come with git, GCC, and Python installed, whereas with Mac, you will likely have to install them yourself. You can check whether they are each installed by running:

```shell
git --version
clang --version
gcc --version
python --version
```

If any of these give you an error, you probably don't have that tool. For Python, you might also have a version which is too old. You can remedy these issues by running one of the below commands in your terminal, based on your operating system. 

```shell
# Linux:
sudo apt install missing-package-name # brand new install
sudo apt upgrade package-w-insufficient-version # upgrade version

# Mac:
xcode-select --install # gets you CLI tools (git, clang, make, some others)
brew install pyenv # gets a python environment manager, followed by:
pyenv install 3.12.4 && pyenv global 3.12.4 # install python 3.12.4 
```

## 1.2. Installing F Prime
TODO

## 1.3. Cloning the Repo for Development
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

Finally, once you have code ready for testing on hardware (i.e. compiled and working on your local F' instance), push your code to remote and create a pull request for your branch to dev (make sure to merge dev into your branch if it has been updated!) at [the pull requests page](https://github.com/ASEN-Capstone-Green/asen4018-green-fsw/compare) and reach out to Luke or your subsystem lead. 

## 1.4. Flashing FSW onto the Flight Module


# 2. Workflow

## 2.1. Manifests and Versioning

## 2.2. Tags
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

## 2.3. Some Helpful Aliases
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
