copy pasta from https://github.com/64-Dev-Docker/submodule-dotnet and modified for python


# Developing in DevContainers

## Getting Windows Git Credentials into WSL2

```bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"
```

[source](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-git#git-credential-manager-setup)

## Getting a .devcontainer.json into a repo

### Using _git submodules_

This is intended to be used as a git sub-module. 

To use in an existing repo first delete the existing `.devcontainer` folder and commit this change.

```bash
git rm -rf .devcontainer\
```

Then clone and update the .devcontainer submodule.

```bash
cd {root project}
git submodule add git@github.com:VadoseCrane0/submodule-python.git .devcontainer
git submodule init
git submodule update
```

If you make change to the .devcontainer that you want to commit back to the repo.

```bash
cd {project root}/.devcontainer
git add {changes to add}
git commit -m"{commit mesage}"
git push
cd ..
git submodule update
```

## General WSL

- [Configuring WSL](https://docs.microsoft.com/en-us/windows/wsl/wsl-config#configure-global-options-with-wslconfig)

Sone extensions (_GitGraph_) require `socat` to communicate with the host this can be installed with:

```sh
sudo apt-get install socat
```

Executed from the WSL shell.

## Setup and Initial Configuration

This is a quick walk through of setting up a development environment in VS Code using docker images. I don't claim great knowledge on this, I've got them running and they seem to be ok.

* [Visual Sutdio Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)
* [64-Dev-Docker/dev-env (github.com)](https://github.com/64-Dev-Docker/dev-env)
* [Docker Hub](https://hub.docker.com/)
* [go lang docker container configuration (github.com)](https://ygist.github.com/waltiam/c94e2d042cac1e7976ebac9e683f2287)

> To the best of my knowledge this technology does not apply to Visual Studio.

## Issues

If you've run into issues with file ownership:

### Linux Error

If this is your error:

```bash
> git commit -m"clever commit message"
$ fatal: could not open '.git/COMMIT_EDITMSG': Permission denied
```

This should resolve the immediate challenge
```bash
chown -R $(whoami) .
```

A better, and longer term solution would be to review the users in the local and remote docker container.
