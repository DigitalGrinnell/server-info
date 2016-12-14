# server-info
A simple bash script to aid with server maintenance.

This script reqiures 'figlet'.
```bash
apt-get install figlet
yum --nogpgcheck figlet
```

Park a copy of server-info in /usr/local/bin and give it rwxr-xr-x (755) file protection like so... as root:

```bash
curl -o /usr/local/bin/server-info https://raw.githubusercontent.com/DigitalGrinnell/server-info/master/server-info
chmod 755 /usr/local/bin/server-info
if [ -f /etc/server-info.txt ]; then
  echo "/etc/server-info.txt already exists so it was NOT replaced."
else
  curl -o /etc/server-info.txt https://raw.githubusercontent.com/DigitalGrinnell/server-info/master/server-info.txt
  chmod 766 /etc/server-info.txt
fi
echo "All done."

```

Create a symbolic link 'ln -s /usr/local/bin/server-info server' in /usr/local/bin if you like.

Put server maintenance reminders in /etc/server-info.txt (a text file) as you wish.
