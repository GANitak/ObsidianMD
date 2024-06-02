```sh
#!/bin/bash
# Define ANSI color escape codes
GREEN='\033[0;32m'
ORANGE='\033[0;33m'
RED='\033[0;31m'
NC='\033[0m' # No Color/reset

echo -e "${GREEN}Current time in ${ORANGE}UTC-6 ${RED}(Central Time):${NC}"
TZ="America/Chicago" date
echo ##############
echo -e "${GREEN}Current time in ${ORANGE}UTC-7 ${RED}(Mountain Time):${NC}"
TZ="America/Denver" date
echo ##############
echo -e "${GREEN}Current time in ${ORANGE}UTC-8 ${RED}(Pacific Time):${NC}"
TZ="America/Los_Angeles" date
echo ##############
# Create a line break
echo

# Display current time in UTC-5 (Eastern Time)
echo -e "${RED}Current time in UTC-5 (Eastern Time):${NC}"
TZ="America/New_York" date
echo -e "${GREEN}Current time in ${ORANGE}UTC-9 ${RED}(Alaska Time):${NC}"
TZ="America/Anchorage" date
echo ##############
echo -e "${GREEN}Current time in ${ORANGE}UTC-10 ${RED}(Hawaii-Aleutian Standard Time):${NC}"
TZ="Pacific/Honolulu" date
```

cat .bashrc

```sh
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar
# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi


# Set the prompt
export PS1="\[\033[38;5;12m\][\[$(tput sgr0)\]\[\033[38;5;10m\]\u\[$(tput sgr0)\]\[\033[38;5;12m\]@\[$(tput sgr0)\]\[\033[38;5;7m\]\h\[$(tput sgr0)\]\[\033[38;5;12m\]]\[$(tput sgr0)\]\[\033[38;5;15m\]: \[$(tput sgr0)\]\[\033[38;5;7m\]\w\[$(tput sgr0)\]\[\033[38;5;12m\]>\[$(tput sgr0)\]\[\033[38;5;10m\]\\$\[$(tput sgr0)\]\[\033[38;5;15m\] \[$(tput sgr0)"
[ -e "/etc/DIR_COLORS" ] && DIR_COLORS="/etc/DIR_COLORS"
[ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
[ -e "$DIR_COLORS" ] || DIR_COLORS=""
eval "`dircolors -b $DIR_COLORS`"

# ALIAS shortcuts:

alias ls='ls --color=auto'
alias grep='grep --color=auto'
#PS1='[\u@\h \W]\$ '
alias ..="cd .."
alias cd..="cd .."
alias m="vim"
alias ll="ls -la"
alias TZ='~/show_timezone.sh'
#alias t-6="America/Chicago" date
#alias t-9="America/Anchorage" date


# GO modules
export GO111MODULE=on

# HOMEBREW shell (help with protobuf)
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# KIND get Clusters
export PATH="$PATH:/home/ganitak/go/bin/kind"


# DISPLAY STATUS
neofetch
```