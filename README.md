# server-info
A simple bash script to aid with server maintenance.

This script reqiures 'figlet' and 'mdv' (a terminal markdown viewer).
```bash
sudo apt-get install figlet   <-- Ubuntu
sudo yum install --nogpgcheck figlet   <-- CentOS 
pip install mdv  <-- Assuming Python and Pip are available
```

Park a copy of server-info in /usr/local/bin and give it rwxr-xr-x (755) file protection like so... as root:

```bash
curl -o /usr/local/bin/server-info https://raw.githubusercontent.com/DigitalGrinnell/server-info/master/server-info
chmod 755 /usr/local/bin/server-info
if [ -f /etc/server-info.md ]; then
  echo "/etc/server-info.md already exists so it was NOT replaced."
else
  curl -o /etc/server-info.md https://raw.githubusercontent.com/DigitalGrinnell/server-info/master/server-info.md
  chmod 766 /etc/server-info.md
fi
echo "All done."

```

Create a symbolic link 'ln -s /usr/local/bin/server-info server' in /usr/local/bin if you like.

Put server maintenance reminders in /etc/server-info.md (a Markdown file) as you wish.
