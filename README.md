# WORKSPACE SETUP

## MACBOOK

### 1. BASICS

- [Install Chrome](https://www.google.com/intl/en_ca/chrome/)
- [Install Zoom](https://zoom.us/)
- [Install 1Password](https://1password.com/downloads/mac/) 
  > Store the emergency kit saftely (ie. Google Drive)

### 2. CLI

- Terminal, [Install iTerm](https://iterm2.com/)
- Zsh config framework, [Install OhMyZsh](https://github.com/ohmyzsh/ohmyzsh)
- Preferred theme, [Configure OhMyZsh Theme](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#half-life)
- MacOS package manager, [Install Homebrew](https://brew.sh/)
- Load/Unload directory-level environment variables, [Install direnv](https://direnv.net/)
- Put localhost on the internet using ingress-as-a-service [ngrok](https://ngrok.com/)

### 3. DEVELOPMENT ENVIRONMENT

#### 3.1 PYTHON

**Install pyenv**

```
$ brew update && brew install pyenv
```

Append the following to ~/.zshrc

```
# pyenv ----
# To use Homebrew's directories rather than ~/.pyenv
export PYENV_ROOT="/usr/local/var/pyenv"

# To enable shims and autocompletion
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
```

#### 3.2 NODE & NPM

**Install**:

- Super fast JS package management, [Install yarn](https://classic.yarnpkg.com/en/docs/install)
- Node version management, [Install nvm](https://github.com/nvm-sh/nvm#installing-and-updating) 

```
# yarn
npm install --global yarn

# nvm
brew update && brew install nvm
echo '# nvm ----' >> /Users/<username>/.zshrc
echo 'export NVM_DIR=~/.nvm' >> /Users/<username>/.zshrc
echo 'source $(brew --prefix nvm)/nvm.sh' >> /Users/<username>/.zshrc
echo '' >> /Users/<username>/.zshrc
source ~/.zshrc
which nvm
nvm use

# direnv
brew update && brew install direnv
echo '# direnv ----' >> /Users/<username>/.zshrc
echo 'eval "$(direnv hook zsh)"' >> /Users/<username>/.zshrc
echo '' >> /Users/<username>/.zshrc
```

**Prettier**

Follow the links IDE to format on save using Prettier:

- [VSCode](https://prettier.io/docs/en/editors.html#visual-studio-code)
- [WebStorm](https://prettier.io/docs/en/webstorm.html#running-prettier-on-save-using-file-watcher)
- [Emacs](https://prettier.io/docs/en/editors.html#emacs)
- [Vim](https://prettier.io/docs/en/editors.html#vim)
- [Others](https://prettier.io/docs/en/editors.html)

#### 3.3 Golang

```
brew update && brew install golang golang-migrate go-bindata
echo '# golang ----' >> /Users/<username>/.zshrc
echo 'export GOPATH=$HOME/go' >> /Users/<username>/.zshrc
echo 'export PATH=$GOPATH/bin:$PATH' >> /Users/<username>/.zshrc
echo '' >> /Users/<username>/.zshrc
source ~/.zshrc
```

#### 3.N Databases

**Install**:

- [Install DBeaver](https://dbeaver.io/download/)

### 4. GIT

https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

**Generate public/private key pair**

```
$ ssh-keygen -t rsa -b 4096 -C "<your-email-address>"
```

**Ensure ssh-agent is running**

```
$ eval "$(ssh-agent -s)"
$ touch ~/.ssh/config
```

**Append the following to ~/.ssh/config**

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/<prefix>_github
```

```
$ ssh-add -K ~/.ssh/<prefix>_github
```

**GPG signing**

```
$ brew install gnupg
```

Follow instructions here: https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-gpg-key

#### Git branch print to CLI
Since the release of Git 2.16, the `git branch` command runs as paged executable instead of printing to the console. To revert back, update your ~/.gitconfig as follows:
```
$ git config --global pager.branch false
```
_--Credit to https://stackoverflow.com/a/48370253_

### 5. CLOUD PROVIDERS

#### Google Cloud Platform (GCP)

```
brew install --cask google-cloud-sdk

# interact with GCP via gcloud
gcloud auth login
# OR
# code to interact with GCP via SDK
gcloud auth application-default login
```

### 6. MISC

```
$ brew install wget curl tig htop
```
