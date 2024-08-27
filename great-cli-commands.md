⚙️ `tldr`
- Gives you a quick, simple explanation of how to use a command. Like a cheat sheet for the terminal.

⚙️ `sxiv`
- Opens a simple program to view images. 

⚙️ `sudo iotop --processes  --only`
- Shows which processes are using disk I/O. 

⚙️ `diff -Nurs "$1" "$2" | diff-so-fancy`
- Advanced diff output. 

⚙️ `parallel convert {} {.}.jpg ::: *.png`
- Changes all PNG images to JPG format at the same time. 

⚙️ `sudo lsblk --output MODEL,TYPE,NAME,SIZE,MOUNTPOINT,FSTYPE`
- Lists all your disk drives and partitions. 

⚙️ `wkhtmltopdf --enable-local-file-access MY_PRESENTATION.html MY_PRESENTATION.pdf`
- Turns a web page (HTML) into a PDF file. 

⚙️ `echo -e "\e[3mpwd\e[0m" && ls -A -F --group-directories-first --sort=extension --color=always`
- Shows current folder and lists all files in a neat, colorful way. 

⚙️ `curl ipinfo.io/ip; echo \; hostname -I | cut -d\ \ -f1; echo \; python3 -m http.server 8095`
- Shows which processes are using disk I/O.

⚙️ `viddy "echo  'Private  +  Shared    =  RAM used    Program'; sudo ps_mem | tac | head -n -1"`
- Constantly updates to show which programs are using the most memory. 

⚙️ `viddy -n 1 -d "echo Temp; sensors 2> /dev/null | grep Core; echo ; echo Freq; cat /proc/cpuinfo | grep \"^[c]pu MHz\""`
- Refreshes every second to show CPU temperature and speed. 

