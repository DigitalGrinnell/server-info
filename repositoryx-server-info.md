This is __/etc/server-info.md.__  Edit this file to include reminders and important information.  
===
Modified: Thursday, September 6, 2018 12:32 PM

**As of 13-October-2017 this server controls the PRODUCTION repository for Digital Grinnell.**  

Copy this file to RepositoryX

- **DRUPAL FILTER**: The Drupal Servlet Filter (auth filter) is configured in
  `/usr/local/fedora/server/config/filter-drupal.xml`

- **TOMCAT**: Fedora and Apache Tomcat (Catalina) are key to this server's operation!
    - Commands available to help manage these include: `sudo service tomcat status|stop|start|restart`
    - Or consider using the Tomcat manager interface in your browser by visiting: http://repositoryX.grinnell.edu:8080/manager and login as fedoraAdmin.
    - Test the Fedora repo at http://repositoryX.grinnell.edu:8080/fedora  

- **LOGS**: Look for problems in `/usr/local/fedora/tomcat/logs/catalina.out` and/or in
  `/usr/local/fedora/server/logs/\*.log` for Fedora, FedoraGSearch and Adjore-Djatoka.  

  @TODO: Add commands to download all logs for editing in Atom.

- **DJATOKA**: Test Adore-Djatoka at http://repositoryX.grinnell.edu:8080/adore-djatoka

- **SOLR and FGSearch**: SOLR administration available at http://repositoryX.grinnell.edu:8080/solr/#/ and
  FedoraGSearch REST at http://repositoryX.grinnell.edu:8080/fedoragsearch/rest.

    - In the FGS REST screen use the 'updateIndex' link and the 'updateIndexFromFoxmlFiles'
    to re-index ALL content (leave the path blank), or 'updateIndex fromPid' for an individual object.  

    - FGS configuration can be found in subdirectories of
    `/usr/local/fedora/tomcat/webapps/fedoragsearch/WEB-INF/classes/fgsconfigFinal` and the FGSIndex
    is in `/usr/local/fedora/solr/collection1/data/index`.  

    - Islandora transforms are in the `.../fgsconfigFinal/index/FgsIndex/islandora_transforms` directory.  

    - Our **Solr schema** is defined in `/usr/local/fedora/solr/collection1/conf/schema.xml`.

    - For lots of good info check out http://v2p2dev.to.cnr.it/doku.php?id=repo371:base, especially the Fedora fix in the last section!  

- **MULTI-TAIL**: For multitail use see http://www.tecmint.com/view-multiple-files-in-linux/ and try this...  
`multitail -s 3 /tomcat.log /fedora.log /djatoka.log`

- **PID NUMBERS**: Highest Fedora object PID numbers are held in MySQL, database 'Fedora' and table 'pidGen'.

- **MySQL**: Use this to login to MySQL here... `mysql --user=root --password=<DG's Fedora Password> fedora3`.

- **DISK USAGE**: To find large files...
 `du -k | sort -n | perl -ne 'if ( /^(\d+)\s+(.*$)/){$l=log($1+.1);$m=int($l/log(1024));  
   printf ("%6.1f\t%s\t%25s %s\n",($1/(2**(10*$m))),(("K","M","G","T","P")[$m]),"*"x (1.5*$l),$2);}'`

- **GENIUS!**: On 7-Oct-2017 I took steps from https://groups.google.com/d/msg/islandora/rkuFz1lqfQQ/pbwyABQmAQAJ
  to move the ActiveMQ storage off of `/usr/local/fedora/data` to `/data2`.  It's a brilliant move.

- May 2017 At Hamilton College working in...
  `/usr/local/fedora/tomcat/webapps/fedoragsearch/WEB-INF/classes/fgsconfigFinal/index`  
  Cloned from git...
  `sudo git clone https://github.com/discoverygarden/basic-solr-config.git FgsIndex`  
  Then from the resulting FgsIndex directory... `sudo git clone https://github.com/discoverygarden/islandora_transforms.git`

  ---
