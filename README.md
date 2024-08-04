# bashrc

```
# Função para obter a branch atual do git (se existir)
get_git_branch() {
  local branch=$(git symbolic-ref --short HEAD 2>/dev/null)
  if [ -n "$branch" ]; then
    echo " (${branch})"
  fi
}

# Função para obter o nome de domínio
get_domain() {
  local domain=$(uname -n)
  if [ -z "$domain" ]; then
    domain="localdomain"
  fi
  echo $domain
}

# Definindo as cores
bold=$(tput bold)
normal=$(tput sgr0)
white='\[\033[1;37m\]'
blue='\[\033[1;34m\]'
green='\[\033[1;32m\]'

# Configurando o prompt PS1
export PS1="${bold}${white}\u@$(get_domain)${normal} ${bold}${blue}\w${normal}${bold}${green}\$(get_git_branch)${normal}: "

# Fonte de cores para verificar a cor
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```
