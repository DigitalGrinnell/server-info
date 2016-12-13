# server-info
A simple bash script to aid with server maintenance.

This script reqiures 'figlet'.

Park a copy of server-info in /usr/local/bin and give it rwxr-xr-x (755) file protection like so... as root:

  cd /usr/local/bin
  curl -o filename raw-link-to-file
  
Create a symbolic link 'ln -s /usr/local/bin/server-info server' in /usr/local/bin if you like.
Put server maintenance reminders in /etc/server-info (a text file) as you wish.
