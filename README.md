# git-submodules-template

Simple submodule template using git 

## How to setup sub modules 

```
git clone https://github.com/Crypto-lyon/git-submodules-template.git
cd git-submodules-template
git submodule add https://github.com/Crypto-lyon/git-submodule-A.git abi
git submodule add https://github.com/Crypto-lyon/git-submodule-B.git utils
```

Notice that the `.gitmodules` file is now listing git submodules.


## How to retreive sub modules 

```
git clone https://github.com/Crypto-lyon/git-submodules-template.git
cd git-submodules-template
git submodule init && git submodule update
# to update all submodules:
git submodule update --recursive --remote
```

## How to delete a sub module

Example with _utils_ submodule.

Delete the relevant section from the `.gitmodules` file. The section would look similar to: 
```
[submodule "utils"]
	path = utils
	url = https://github.com/Crypto-lyon/git-submodule-B.git
```
Stage the `.gitmodules` changes via command line using:  `git add .gitmodules`.

Delete the relevant section from `.git/config`, which will look like:

```
[submodule "utils"]
	active = true
	url = https://github.com/Crypto-lyon/git-submodule-B.git
```

Run `git rm --cached utils`

Run `rm -rf .git/modules/utils`

Commit the changes.

Delete the now untracked submodule files `rm -rf utils`.

#### Source:

https://davidwalsh.name/git-remove-submodule