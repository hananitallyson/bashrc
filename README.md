# bashrc

```
# Definindo as cores
bold=$(tput bold)
normal=$(tput sgr0)
white='\[\033[1;37m\]'
blue='\[\033[1;34m\]'
green='\[\033[1;32m\]'
gray='\[\033[1;30m\]'
red='\[\033[1;31m\]'

# Função para obter a branch atual do git (se existir)
get_git_branch() {
  local branch=$(git symbolic-ref --short HEAD 2>/dev/null)
  if [ -n "$branch" ]; then
    echo " ( ${branch})"
  fi
}

# Função para obter o nome de domínio
get_domain() {
  local domain=$(uname -n)
  if [ -z "$domain" ]; then
    domain="localdomain"
  fi
  echo "$domain"
}

# Função para configurar o prompt
function prompt_command {
  PS1="${bold}${white}\u@$(get_domain)${normal} ${bold}${gray}in${normal} ${bold}${blue}\w${normal}${bold}${green}\$(get_git_branch)${normal}: "
}

# Configurando o prompt PS1
PROMPT_COMMAND=prompt_command

# Habilita o autocomplete
if [ -f /etc/bash_completion ]; then
  . /etc/bash_completion
fi

# Outros aliases
alias ..="cd ../"
alias ...="cd ../../"
alias ....="cd ../../../"
alias .....="cd ../../../../"

# Ativa a colorização do `ls`
alias ls="ls --color=auto"

# Fonte de cores para verificar a cor
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad

# Habilita o histórico compartilhado e melhorias de linha de comando
export HISTCONTROL=ignoredups:erasedups
export HISTSIZE=10000
export HISTFILESIZE=10000
shopt -s histappend

```
