# Developing in DevContainers

## Setting up Git Credentials

https://code.visualstudio.com/docs/remote/containers#_sharing-git-credentials-with-your-container

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