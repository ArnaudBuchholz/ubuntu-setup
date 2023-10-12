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
