#
#    __                                
#   (  )                               
# \ _\/_,'    HONEYGUIDE ZSH CONFIG    
#--("))))))= -.._.-'-.._.-'-.._.-'-.._.
#     \\   
#
#

#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Common Settings
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
autoload -U colors && colors
#PS1='%B%F{red}❯ %f%b' # for root
PS1='%B%F{green}❯ %f%b'
autoload -U promptinit
promptinit

setopt AUTO_CD
setopt auto_cd
setopt extended_glob
setopt +o nomatch
unsetopt CASE_GLOB

autoload -Uz compinit
compinit
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}' 

# custom Right prompt
#setopt PROMPT_SUBST PROMPT_CR PROMPT_SP
#typeset -a no_rprompt_commands=(ls pwd e s d t nn)
#zsh_last_command=""
#preexec() { zsh_last_command="${1%% *}" }
#precmd() {
#    (( ${(@)~no_rprompt_commands[(Ie)$zsh_last_command]} )) && \
#    RPROMPT='' || RPROMPT='%F{#04548a}%1~%f'
#}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => CUSTOM HISTORY
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
HISTFILE=~/.histfile
HISTSIZE=3000
SAVEHIST=3000

setopt HIST_IGNORE_ALL_DUPS 
setopt INC_APPEND_HISTORY  
setopt EXTENDED_HISTORY   
setopt HIST_EXPIRE_DUPS_FIRST
setopt HIST_FIND_NO_DUPS    
setopt HIST_IGNORE_SPACE   
setopt SHARE_HISTORY      
HISTORY_IGNORE='(vh|s|e|vz|n|d)' 

# custom history file
function vh {
    temp_file=$(mktemp /tmp/histfile.XXXXXX)
    temp_view_file=$(mktemp /tmp/histfile_view.XXXXXX)

    awk -F':' '
    /^[0-9]{2}-[0-9]{2}-[0-9]{2} [0-9]{2}:[0-9]{2}/ { print; next }
    {
        cmd=$3
        sub(/^0;/, "", cmd)
        date=strftime("%y-%m-%d %H:%M", $2)
        print date "| " cmd
    }' ~/.histfile > "$temp_file" && mv "$temp_file" "$temp_view_file"

    vim "$temp_view_file"
    rm "$temp_view_file"
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => KEY BINDINGS
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
bindkey '\C-a' backward-char          # Ctrl+A to move cursor one character backward
bindkey "\C-o" accept-line            # Ctrl+F to accept the current line (like Enter)
bindkey '\C-h' up-line-or-history     # Ctrl+H to move up in history
bindkey '\C-g' down-line-or-history   # Ctrl+G to move down in history
bindkey '^[[27;5;44~' backward-word   # Ctrl+, jump word left
bindkey '^[[27;5;46~' forward-word    # Ctrl+. jump word right

# Function to delete current word or previous word
delete-word-back-or-current() {
   [[ $CURSOR -eq 0 || "${LBUFFER[-1]}" =~ [[:space:]] ]] &&
   zle backward-kill-word || { zle backward-word; zle kill-word }
}
zle -N delete-word-back-or-current
bindkey '^\' delete-word-back-or-current  # Ctrl+\ to delete current or previous word



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => ADDITIONAL COMMON SETTINGS
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
alias -s mp4='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s mkv='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s mp3='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s avi='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s grec='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s mov='mplayer -af scaletempo -really-quiet -vo xv -pausing 2'
alias -s pdf='evince'
alias -s djvu='evince'
alias -s txt='vim'
alias -s odp='libreoffice'
alias -s pptx='libreoffice'

export EDITOR=vim
export VISUAL=vim
export PATH=$PATH:/home/honeyguide/Python_scripts/
stty -ixon       # disable Ctrl-S/Q flow control, freeing them for other uses



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Moving and Basic System Commands
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
#alias ls='echo -e "\e[3m`pwd`\e[0m" && ls -A -F --group-directories-first --sort=extension --color=always'
alias l='\ls | nl'
alias cal='ncal'
alias j='\cd ../; facad;'
#alias jj='\cd ../../; ls;'
alias jj='\cd -; ls;'

function f {
  if [[ $1 != '' && $1 != '/' && $1 != */ ]]; then
      cd $1 && facad
  elif [[ $1 == '/' ]]; then
    \cd / && facad
  elif [[ $1 == */ ]]; then
    \cd $1 && facad
  elif [[ $1 == '-' ]]; then
    \cd -
  else
    ls
  fi
}

alias s1='systemctl poweroff'
alias s2='systemctl suspend'
alias s3='sudo reboot'
function sus {
    #echo "systemctl suspend after $1 minute" && sudo sleep $1m && sudo systemctl suspend
    echo 'disabled' | sudo tee /sys/bus/usb/devices/usb1/1-5/power/wakeup;
    sudo systemctl suspend
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Basic Aliases
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
alias vr='vim ~/Python_scripts/rp'
alias vv='vim ~/.vimrc'
alias vz='vim ~/.zshrc'
alias vsw='vim /home/honeyguide/.config/sway/config'
alias vf='vim /home/honeyguide/.config/foot/foot.ini'
alias ii='swaymsg reload'
#alias xx='xrdb /home/honeyguide/.Xresources'
alias zz='source ~/.zshrc'
alias cp='cp -r'

alias x='firefox &; disown;exit'
alias pale='palemoon &; disown;exit'
alias g='google-chrome-stable &; disown;exit'
alias g2='chromium-browser &; disown;exit'
alias qb='qbittorrent &; disown;exit'
alias slimjet='flashpeak-slimjet &; disown;exit'

alias lsd='ls -d */'
alias lsff='echo "\nFiles:"; \ls -p | grep -v /|column; echo "\nDirectories-> "; tree -d -L 2|column; echo "\n";'

alias to='\cd /mnt/hddtb; ls'
alias to1='\cd ~/Desktop/Labour && ls'
alias to2='\cd ~/Desktop/Leisure && ls'

alias size='du -sh'
alias gsm='xfce4-taskmanager &; disown;exit'
alias tm='xfce4-taskmanager &; disown;exit'

function fp {
  local file_path="$1"
  if [[ -e "$file_path" ]]; then
    local full_path=$(readlink -f "$file_path")
    echo " " 
    echo "$full_path"
    echo " " 
  else
    echo "File does not exist"
  fi  
}

alias ht='htop --sort-key=PERCENT_CPU'
alias rm='sudo rm -R'
alias nc='ncal -M -3'
alias y='yes'

alias fss='sudo lsblk --output MODEL,TYPE,NAME,SIZE,MOUNTPOINT,FSTYPE'
alias rec='arecord -vv -fdat'
alias ff='ffmpeg -hide_banner -i'
alias tl='tldr'
alias i='cd `\cat ~/Desktop/.for_cd`; ls'
#alias cw='watch -n.99 "echo 'Temp'; sensors 2> /dev/null | grep Core; echo ''; echo 'Freq'; cat /proc/cpuinfo | grep \"^[c]pu MHz\""'
alias cw='viddy -n 1 -d "echo 'Temp'; sensors 2> /dev/null | grep Core; echo ''; echo 'Freq'; cat /proc/cpuinfo | grep \"^[c]pu MHz\""'
alias vm='virt-manager &; disown;exit'
alias r='ranger ./'
alias homeserv="curl ipinfo.io/ip; echo ''; hostname -I | cut -d' ' -f1; echo ''; python3 -m http.server 8095" # homeserv

alias viber='/opt/viber/Viber &; disown;exit'

alias feh_bg='feh --bg-scale /home/honeyguide/Pictures/Back/back0.png'

#alias cat='batcat --theme="Coldark-Cold"'
alias bt='urxvt -e btop &; disown; exit'
alias iotop='urxvt -bg "[80]#000000" -fg white -tr -sh 50 -e sudo iotop --only --processes &; disown; exit'

alias qp='pwd | xclip -selection primary'

alias lazydocker='urxvt -bg "[80]#000000" -fg white -tr -sh 20 -e lazydocker &; disown; exit'



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Large functions
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# Install package
function rpi {
    if [ -z "$1" ]; then
        echo "Please use rpi with a package name as an argument."
    else
        sudo dnf install -y $1 && echo '' && rpm -ql $1
    fi
}

# Remove package
#function rpr {
#   sudo dnf remove -y $1 && sudo dnf autoremove -y
#}

# rpr function
# Remove package, unused dependencies and associated files
# Dependencies: fdfind
function rpr() {
    local pack="$1"
    local config_dirs=("/etc" "/usr/share" "$HOME")
    local mime_db="/usr/share/mime"

    # Check if the terminal supports color
    if [ -t 1 ] && [ -n "$TERM" ] && [ "$TERM" != "dumb" ]; then
        local bold="\033[1m"
        local normal="\033[0m"
    else
        local bold=""
        local normal=""
    fi

    echo -e "${bold}The following package and its dependencies will be removed:${normal}"
    sudo dnf remove --assumeno "$pack"
    echo -n "${bold}Proceed with removal? (y/n) ${normal}"
    read -r response
    if [[ ! $response =~ ^[Yy]$ ]]; then
        echo "${bold}Removal cancelled.${normal}"
        return 1
    fi
    sudo dnf remove -y "$pack"
    echo
    echo -e "${bold}Searching packages that no longer needed and can be removed:${normal}"
    sudo dnf autoremove --assumeno
    echo -n "${bold}Proceed with autoremoval of unused dependencies? (y/n) ${normal}"
    read -r response
    if [[ $response =~ ^[Yy]$ ]]; then
        sudo dnf autoremove -y
    else
        echo "${bold}Autoremoval skipped.${normal}"
    fi
    # Remove configuration files
    for dir in "${config_dirs[@]}"; do
        sudo fd --hidden --no-ignore "$pack" "$dir" -x sudo rm -rf {}
    done
    echo "${bold}Configs associated with $pack removed.${normal}"

    # Find remaining files
    local files_to_remove=($(sudo fd --hidden --no-ignore "$pack" / 2>/dev/null))
    if (( ${#files_to_remove[@]} > 0 )); then
        echo "${bold}Found the following files:${normal}"
        for file in "${files_to_remove[@]}"; do
            echo "$file"
            echo -n "${bold}Delete this file? (y/n) ${normal}"
            read -r response
            if [[ $response =~ ^[Yy]$ ]]; then
                sudo rm -rf "$file"
            else
                echo "${bold}Skipped deletion of $file${normal}"
            fi
        done
    fi

    # Update icon cache and databases
    sudo update-desktop-database
    sudo update-mime-database "$mime_db"
    echo "${bold}Cleanup completed.${normal}"
}

# List packages that are ready to upgrade
function rpupdl {
   sudo dnf check-update
   sudo dnf list --upgrades | nl
}

# Full upgrade
function rpflupgr() {
    sudo dnf upgrade --refresh -y
    sudo dnf autoremove -y
    sudo dnf clean all
}

# List content of package
function rpl {
   #rpm -ql $1
   rpm -ql $1 | grep -vE '^/usr/share/|^/usr/lib/\.build-id/'
}

# Search packages with specific substring
function rps {
    pkg=$1
    dnf search "$pkg" | sed -E 's/^(.*)\.(x86_64|noarch|i686) : /\1 # /' | awk '{printf "%-20s # %s\n", $1, substr($0, index($0, "#") + 2)}'
    echo -e "\033[1mFound packages in Rep: $(dnf search "$pkg" | wc -l)\033[0m"
}

# Search packages with specific substring locally
function rpsl {
    dnf list installed | grep "$1" | cut -d'.' -f1 | nl
}

# Search packages with exact name
rpst () {
    pkg=$1
    dnf list --showduplicates "$pkg" | sed -E 's/^(.*)\.(x86_64|noarch|i686) .*/\1/' | awk '{printf "%-20s # %s\n", $1, substr($0, index($0, "#") + 2)}'
}

# List of snap packages
rpflat () {
    snap list --all | awk 'NR>1 {print $1, $2}' | column -t | nl
}

# Package statistics
function rpstat {
    echo "Packages installed: $(dnf list installed | wc -l) (Total avail: $(dnf list | wc -l))"
    echo "Libs installed: $(dnf list installed | grep 'lib' | wc -l)"
    echo "Python modules: $(pip3 list | wc -l)"
    echo "Services running: $(systemctl list-units --type=service --state=running | grep -c .service)"
    echo "Installed by user: $(dnf history userinstalled | wc -l)"
    echo "Snap: $(( $(snap list | wc -l) - 1 ))"
}

# Find the package that provides a given command or file
function rpw {
    echo Pack: $(dnf provides $(which $1 2>/dev/null || echo $1) 2>/dev/null | grep -m1 Fedora | awk '{print $1}' | sed 's/\..*$//' || echo 'None')
}

# Show package dependencies 
function rpdn {
    local pkg=$1
    local description=$(dnf info $pkg 2>/dev/null | awk -F': ' '/^Summary/ {print $2}')
    printf "\033[1m%-19s # %s\033[0m\n" "$pkg" "$description"

    local deps=$(dnf repoquery --requires --resolve "$pkg" 2>/dev/null | sort -u | grep -v "^$pkg-")
    if [[ -z "$deps" ]]; then
        echo "No package dependencies found."
        echo "Showing library dependencies:"
        deps=$(ldd $(which $pkg 2>/dev/null) 2>/dev/null | awk '{print $1}' | sort -u)
    fi

    echo "$deps" | while read -r dep; do
        local clean_dep=${dep%% [<>=]*}
        local desc=$(dnf info "$clean_dep" 2>/dev/null | awk -F': ' '/^Summary/ {print $2; exit}')
        printf "  %-17s %s\n" "$clean_dep" "${desc:+# $desc}"
    done

    local total=$(echo "$deps" | wc -l)
    echo "\033[1mTotal Number of dependencies: $total\033[0m"
}

# List installed packages dependent on another
function rpdr {
    pkg=$1
    description=$(dnf info $1 2>/dev/null | grep 'Summary' | sed 's/Summary *: //')
    printf "\033[1m%-24s # %s\033[0m\n" "$pkg" "$description"
    dnf repoquery --installed --whatrequires "$pkg" | \
    while read -r dep; do
        desc=$(dnf info "$dep" 2>/dev/null | grep 'Summary' | sed 's/Summary *: //')
        printf "%-24s # %s\n" "$dep" "$desc"
    done
    dependency_count=$(dnf repoquery --installed --whatrequires "$pkg" | wc -l)
    echo "\033[1mDependency for: $dependency_count packages\033[0m"
}

# List repo packages depending on another
function rpdrall {
    pkg=$1
    description=$(dnf info $1 2>/dev/null | grep 'Summary' | sed 's/Summary *: //')
    printf "\033[1m%-19s # %s\033[0m\n" "$pkg" "$description"
    dnf repoquery --whatrequires "$pkg" | \
    while read -r dep; do
        desc=$(dnf info "$dep" 2>/dev/null | grep 'Summary' | sed 's/Summary *: //')
        printf "  %-17s # %s\n" "$dep" "$desc"
    done
    echo "\033[1mDependency for: $(dnf repoquery --whatrequires "$pkg" | wc -l)\033[0m"
}

# Full info about package
function rpinfo() {
    if [[ -z "$1" ]]; then
        echo "Please use rpinfo with a package name as an argument"
        return 1
    fi
    local package="$1"
    local installed_status
    local description

    if dnf list installed "$package" &>/dev/null; then
        installed_status="installed: YES"
    else
        installed_status="installed: NO"
    fi

    description=$(dnf info "$package" 2>/dev/null | sed -n 's/Summary *: //p')

    echo "\\033[1m$package ($installed_status) - $description\\033[0m"
    echo ''

    dnf info $package | awk -F': ' '
    BEGIN {
        BOLD="\033[1m";
        NORMAL="\033[0m";
    }
    {
        if ($1 ~ /Name|Version|Release|Architecture|Size|Source|Repository|Summary|URL|License|Description/) {
            gsub(/^ */, "", $1);
            if ($1 == "Description") {
                print BOLD $1 NORMAL ":";
                getline;
                while ($0 !~ /^$/) {
                    print "        " $0;
                    if (getline <= 0) {
                        break;
                    }
                }
            } else {
                print BOLD $1 NORMAL ": " $2;
            }
        }
    }'
    echo ''

    echo "Files provided by the package:"
    dnf repoquery -l "$package" 2>/dev/null
}


# Get info about command or package
function wh() {
    local cmd_type cmd base result size desc contents alias_def
    cmd_type=$(whence -w "$1" | cut -d' ' -f2)
    case "$cmd_type" in
        alias)
            echo "Type: Alias"
            alias_def=$(alias "$1" | cut -d'=' -f2- | tr -d "'" 2>/dev/null)
            if [[ -n "$alias_def" ]]; then
                echo "${alias_def#*=}"
            else
                alias_def=$(which "$1" 2>/dev/null)
                if [[ -n "$alias_def" ]]; then
                    echo "Comm: ${alias_def#*=}"
                fi
            fi
            ;;
        builtin)
            echo "Type: Built-in"
            echo "Comm: $(alias | /usr/bin/which --tty-only --read-alias --show-tilde --show-dot $1)" || echo "No manual entry for $1"
            ;;
        function)
            echo "Type: Function"
            whence -f "$1"
            ;;
        command)
            cmd=$(whence -p "$1")
            echo "Link: $cmd"
            base=$(readlink -f "$cmd")
            echo "Base: $base"
            if [[ -x "$base" ]]; then
                result=$(file -b "$cmd" | cut -d',' -f1)
                echo "Type: $result"
            else
                echo "Type: $(file -b "$cmd" | cut -d',' -f1)"
            fi
            echo "Pack: $(rpm -qf "$base" 2>/dev/null)"
            size=$(du -sh "$base" 2>/dev/null | cut -f1)
            echo "Size: ${size:-N/A}"
            ;;
        *)
            if [[ "$1" == "alias" ]]; then
                cmd="/usr/bin/alias"
                echo "Link: $cmd"
                echo "Base: $cmd"
                echo "Type: $(file -b "$cmd" | cut -d',' -f1)"
                echo "Pack: $(rpm -qf "$cmd" 2>/dev/null)"
                size=$(du -sh "$cmd" 2>/dev/null | cut -f1)
                echo "Size: ${size:-N/A}"
            elif rpm -q "$1" &>/dev/null; then
                if rpm -ql "$1" | grep -q '\.so'; then
                    echo "Type: Library package"
                else
                    echo "Type: Program package"
                fi
                desc=$(rpm -qi "$1" | awk -F': ' '/^Summary/ {print $2}')
                echo "Desc: $desc"
                contents=$(rpm -ql "$1" | grep '\.so' | head -n 5)
                if [[ -n "$contents" ]]; then
                    echo "Cont: $(echo "$contents" | sed '2~1s/^/      /')"
                fi
            else
                echo "This entity doesn't exist"
            fi
            ;;
    esac
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Autocompletion functions
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
_wh() {
    local -a completions
    completions+=(${(k)aliases})
    completions+=(${(k)builtins})
    completions+=(${(k)functions})
    completions+=(${(k)commands})
    compadd -a completions
}
compdef _wh wh


_rpdn() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpdn rpdn

_rpdr() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpdr rpdr

_rpdrall() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpdrall rpdrall

_rps() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rps rps

_rpl() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpl rpl

_rpi() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpi rpi

_rpr() { 
   compadd $(dnf list installed | awk '{print $1}' | grep -v "@" | tail -n +2 | sed 's/\..*$//')
} 
compdef _rpr rpr

_cht() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _cht cht

_t() { 
  _files -g '*/'
} 
compdef _t t

_rpinfo() { 
   compadd $(dpkg -l | awk '{print $2}' | tail -n +6)
} 
compdef _rpinfo rpinfo



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => SMALL FUNCTIONS
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# https://github.com/yellow-footed-honeyguide/unpak
alias un='unpak'

function mem {
   viddy "echo  'Private  +  Shared    =  RAM used    Program'; sudo ps_mem | tac | head -n -1"
}

function fbig {
    find ./ -xdev -type f -size +$@G | sed -e 's/"/"\\""/g' -e 's/.*/"&"/' |
    xargs du -sh | sort -rn | sed -e 's/.*\.$/Files not found/g'
}

function flate {
  ls -Art | tail -n $@ |
  sed -e 's/"/"\\""/g' -e 's/.*/"&"/' |
  xargs stat -c "%y %n" | sort -n
}

function rmbut {
     mkdir ../.rmbut &&
     mv $1 ../.rmbut &&
     rm * &&
     mv ../.rmbut/$1 ./ &&
     rm ../.rmbut
}

function gre {
    grep -nir $1 * | sed '/Binary/d' | nl 
}

function loc {
    fd "$1" . 2>&1 | grep -v "Permission denied" | nl
}

function rpfb() {
  if [[ -z "$1" ]]; then
    echo "Use argument"
    return 1
  fi

  # Shared Libraries
  echo "\033[1mShared Libraries:\033[0m"
  if ! fd --type f --regex "$1(-\\d+\\.\\d+)?\\.so(\\.\[0-9\]+)?" /usr/lib /lib 2> /dev/null | grep -q .; then
    echo "Nothing found"
  else
    fd --type f --regex "$1(-\\d+\\.\\d+)?\\.so(\\.\[0-9\]+)?" /usr/lib /lib 2> /dev/null
  fi

  echo ""

  # Executables
  echo "\033[1mExecutables:\033[0m"
  if ! fd --type executable --glob "*$1*" -E /snap -E /var -E /usr/lib -E /usr/lib32 -E "*lib*" / 2>/dev/null | nl | grep -q .; then
    echo "Nothing found"
  else
    fd --type executable --glob "*$1*" -E /snap -E /var -E /usr/lib -E /usr/lib32 -E "*lib*" / 2>/dev/null | nl
  fi
}


function mir {
  img2pdf * --output slideshow.pdf && evince slideshow.pdf && rm ./slideshow.pdf
}

function ca {
  \cat *.mp3  | ffmpeg  -i pipe: -c:a copy -c:v copy $1 && mv $1 .. && cd .. && ls
}

di () {
   echo "\033[1m`file ./$1`\033[0m" && udevadm info -a --name ./$1 | sed '/""/d' | sed -E -e '/Udevadm|walks|found|rule|single/d' | sed '/looking/d' | sed '/^$/d' | grep -E 'KERNEL|SUBSYSTEM|SUBSYSTEMS|DRIVERS|interface|vendor|device|idVendor|idProduct|manufacturer|product|name|phys|path|speed|model|firmware'
}

function cht {
    /opt/cht.sh $1 | sed 's/\x1B\[[0-9;]\{1,\}[A-Za-z]//g' > ~/.cheat/temp_output_cht_sh && vim ~/.cheat/temp_output_cht_sh && clear && pwd
}

function gc {
   gcc $1 && ./a.out
}


function na {
    filename=$1;
    filename="${filename%.s}";
    nasm -f elf64 -o $filename.o $filename.s && ld -o $filename $filename.o && ./$filename && rm ./*.o
}

function di() {
    diff -Nur "$1" "$2" | diff-so-fancy
}

# Set window title for terminal emulators
# Usage: add to .zshrc and ensure zsh hooks are loaded
set_win_title() {
    case "$TERM" in
        foot*|xterm*|rxvt*|alacritty*)
            if [[ "$1" =~ ^vim.* ]]; then
                # Special handling for vim: show edited file name
                print -Pn "\e]0;vim: ${1#vim }\a"
            elif [[ -n "$1" ]]; then
                # For other commands: show the command name
                print -Pn "\e]0;${1%% *}\a"
            else
                # Default: show current directory
                print -Pn "\e]0;%~\a"
            fi
            ;;
    esac
}
# Set window title to current directory before each prompt
set_win_title_precmd() { print -Pn "\e]0;%~\a" }
# Load zsh hooks
autoload -Uz add-zsh-hook
add-zsh-hook preexec set_win_title
add-zsh-hook precmd set_win_title_precmd



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Systemd functions
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
rpservs () {
  # STEP 1. List running services using systemctl and format the output
  systemctl list-units --type=service --state=running --no-pager | grep service | sed 's/loaded active running//g' | \
  awk '{print "\n\033[1m" NR " | " $1;

  # STEP 2.  Extract and display the Description of the service
  system("systemctl show -p Description " $1 " | \
  sed \"s/Description=//\" | \
  awk \"{print \\\"\033[0mDesc: \\\" \\$0}\"");

  # STEP 3. Extract and display the ExecStart (binary path) of the service
  system("systemctl cat " $1 " | \
  grep -E \"^ExecStart=\" | \
  sed \"s/ExecStart=//\" | \
  awk \"{gsub(/\\\\.\\\\//, \\\" \\\"); print \\\"Exec: \\\" \\$0}\"");

  # STEP 4. Extract and display the actual binary file path (BinA) using readlink -f
  system("systemctl cat " $1 " | \
  grep -E \"^ExecStart=\" | \
  sed \"s/ExecStart=//\" | \
  awk \"{gsub(/\\\\.\\\\//, \\\" \\\"); system(\\\"readlink 2>/dev/null -f \\\" \\$1)}\" | \
  awk \"{print \\\"BinA: \\\" \\$0}\"");

  # STEP 5. Extract the binary file size (Size) of the service
  system("systemctl cat " $1 " | \
  grep -E \"^ExecStart=\" | \
  sed \"s/ExecStart=//\" | \
  awk \"{gsub(/\\\\.\\\\//, \\\" \\\"); system(\\\"du 2>/dev/null -sh \\\" \\$1)}\" | \
  awk \"{print \\\"Size: \\\" \\$1}\"");

  # STEP 6. Extract and display the startup time of the service using systemd-analyze blame
  # system("systemd-analyze blame | grep " $1 " | \
  # awk \"{print \\\"Time: \\\" \\$1}\"");

  # STEP 7. Extract and display the config file path (FragmentPath) of the service
  system("systemctl show " $1 " -p FragmentPath | \
  sed \"s/FragmentPath=//\" | \
  awk \"{print \\\"Conf: \\\" \\$0}\"");}'
}

rpblame() {
  systemd-analyze blame  --no-pager | nl
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Python things
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
alias py='python3'
alias spu='sudo python3 -m pip install --upgrade'
alias spr='sudo python3 -m pip uninstall'
alias spsh='sudo python3 -m pip show'
alias spf='sudo python3 -m pip freeze | nl'

function spi { 
  sudo python3 -m pip install $1 --break-system-packages 
}

function spv {
  sudo python3 -m pip install  $1==
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Mplayer things
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
alias mp="mplayer -af scaletempo -really-quiet -vo xv -pausing 2"
alias mptime="mplayer -af scaletempo -really-quiet -vo xv -pausing 2 -ss"
alias mpv="mplayer -af scaletempo -really-quiet -vo xv -pausing 2 -ss 00:00:44"
alias mpvg="mplayer -af scaletempo -really-quiet -vo xv -pausing 2 -ss 01:42:45"
alias mpvh="mplayer -af scaletempo -really-quiet -vo xv -pausing 2 -ss 00:03:45"
alias mps='mplayer -af scaletempo -vo xv -pausing 2 -shuffle * 2>/dev/null  | grep Playing'
function mpr {
 echo '' && mprr $1 && echo '' && ls
}
function mprs {
 echo '' && mprr -slave -input file=/tmp/mplayer-control $1 && echo '' && ls
}



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => VI-MODE
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
bindkey -v

# Function to update prompt based on vi mode
function zle-line-init zle-keymap-select {
   case ${KEYMAP} in
       vicmd)
           PROMPT='%B%F{green}norm❯ %f%b'
           ;;
       main|viins)
           PROMPT='%B%F{green}edit❯ %f%b'
           ;;
   esac
   zle reset-prompt
}
zle -N zle-line-init
zle -N zle-keymap-select

# Always start in insert mode and set the prompt accordingly
zle-line-init() {
   zle -K viins
   PROMPT='%B%F{green}edit❯ %f%b'
   zle reset-prompt
}
zle -N zle-line-init

# Switch between normal and edit mode with Ctrl+F only
bindkey -M viins '^F' vi-cmd-mode
bindkey -M vicmd '^F' vi-insert

# Move to end of line and enter edit mode with 'n'
bindkey -M vicmd 'n' vi-add-eol

# Normal mode keybindings
bindkey -M vicmd 'd' backward-word
bindkey -M vicmd 'k' forward-word
bindkey -M vicmd 'j' accept-line
bindkey -M vicmd ',' undo
bindkey -M vicmd '.' redo
bindkey -M vicmd 'h' up-line-or-history
bindkey -M vicmd 'g' down-line-or-history
bindkey -M vicmd 'c' kill-whole-line
bindkey -M vicmd 'K' beginning-of-line
bindkey -M vicmd 'D' end-of-line
bindkey -M vicmd 'v' kill-word
bindkey -M vicmd 'a' backward-char
bindkey -M vicmd 'w' forward-char
bindkey -M vicmd 'f' delete-char
bindkey -M vicmd 'E' kill-line
bindkey -M vicmd 't' clear-screen

# Function to delete word (regardless of cursor position)
kill-word() {
   zle set-mark-command
   zle forward-word
   zle backward-kill-word
}
zle -N kill-word

# Paste from system primary buffer in normal mode
#bindkey -M vicmd 'j' vi-put-after

# Disable all keys in insert mode except Ctrl+F
#bindkey -rM viins
bindkey -M viins '^F' vi-cmd-mode

# Restrict input in normal mode
bindkey -M vicmd -r 'a-zA-Z0-9'

# Set a short timeout for key sequences
export KEYTIMEOUT=1



#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
# => Misc
#""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
: <<COMMENT
This is examle of multi-lines comments
COMMENT
