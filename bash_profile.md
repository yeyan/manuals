# Bash profile

Install fasd

```bash
brew install fasd
```

Install python

```bash
brew install python
```
Put the following in `~/.bash_profile`

```bash
# Only uncomment this line if you comfortable confortable with vim
# export EDITOR='vim'

# Prefer home brew applications
export PATH="/usr/local/opt/python/libexec/bin:$PATH"

# Terminal colors

export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced

# Fasd

alias a='fasd -a'        # any
alias s='fasd -si'       # show / search / select
alias d='fasd -d'        # directory
alias f='fasd -f'        # file
alias sd='fasd -sid'     # interactive directory selection
alias sf='fasd -sif'     # interactive file selection
alias z='fasd_cd -d'     # cd, same functionality as j in autojump
alias zz='fasd_cd -d -i' # cd with interactive selection

eval "$(fasd --init auto)"
```
