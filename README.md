# Developing in DevContainers

## Setting up Git Credentials

https://code.visualstudio.com/docs/remote/containers#_sharing-git-credentials-with-your-container

## Set up Git Commit Signing

https://code.visualstudio.com/docs/remote/containers#_sharing-gpg-keys

to have vscode sign your commits Add `"git.enableCommitSigning": true` to `settings.json`

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