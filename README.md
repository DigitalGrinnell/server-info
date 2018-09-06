# server-info
A simple bash script to aid with server maintenance.  Modified: Thursday, September 6, 2018 12:57 PM

This script reqiures 'figlet' and 'mdv' (a terminal markdown viewer).
```
bash
sudo apt-get install figlet   <-- Ubuntu
sudo yum install --nogpgcheck figlet   <-- CentOS
pip install mdv  <-- Assuming Python and Pip are available
```

Park a copy of server-info in /usr/local/bin and give it rwxr-xr-x (755) file protection like so... as root:

```
bash
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

Create a symbolic link `ln -s /usr/local/bin/server-info server` in /usr/local/bin if you like.
---
Put server maintenance reminders in `/etc/server-info.md` (a Markdown file) as you wish.

You can deploy `digital7-server-info.md` to Digital7 with:  
  `rsync -aruvi ./digital7-server-info.md vagrant@132.161.151.50:/home/vagrant/server-info.md --progress` then from a Digital7 terminal use `sudo cp -f ~/server-info.md /etc/server-info.md`  

You can deploy `dgadmin-server-info.md` to DGAdmin with:  
  `rsync -aruvi ./dgadmin-server-info.md vagrant@132.161.151.25:/home/vagrant/server-info.md --progress` then from a DGAdmin terminal use `sudo cp -f ~/server-info.md /etc/server-info.md`  

You can deploy `repositoryx-server-info.md` to RepositoryX with:  
  `rsync -aruvi ./repositoryx-server-info.md vagrant@132.161.151.36:/home/vagrant/server-info.md --progress` then from a RepositoryX terminal use `sudo cp -f ~/server-info.md /etc/server-info.md`  
