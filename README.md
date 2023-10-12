# Ubuntu setup

> General updates
```bash
sudo apt update && sudo apt -y upgrade
sudo update-ca-certificates
``` 

> NVM setup, check latest version on https://github.com/nvm-sh/nvm/releases
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
source ~/.profile
nvm install --lts
```

> Automatic setup of Node.js version based on `.nvmrc`

✏️ `~/.bashrc`
```text
enter_directory() {
 if [[ $PWD == $PREV_PWD ]]; then
 return
 fi
 PREV_PWD=$PWD
 [[ -f ".nvmrc" ]] && nvm use
}
export PROMPT_COMMAND=enter_directory
```

> git
```bash
git config --global user.name "ArnaudBuchholz"
git config --global user.email "arnaud.buchholz@free.fr"
```

> Display current branch

✏️ `~/.bashrc`

*(search and replace)*
```text
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]'
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w'
fi
```
*(add)*
```text
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/🏷️\1/'
}
export PS1="$PS1\[\e[91m\]\$(parse_git_branch)\[\e[00m\]$ "
```
