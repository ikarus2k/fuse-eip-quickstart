Step 1 – Install and Configure product used.  
View the README in 'installs' directory. 
Download the JBoss Fuse product from the Red Hat Customer Support Portal or JBoss.org 
Add to the installs directory.  
Update the zip filename in init.sh in the FUSE_BIN variable.

Step 2 - Run 'init.sh'
From the command prompt run the init script, ./init.sh, from the command line
View output for build success
sample posted to init.sh.output under the support folder 
View the eip-6.0.0.redhat-024.jar in the maven repository

Step 3 - Install and/or Setup JBDS for project import
Download JBDS
Create workspace /home/kpeeples/workspaces/fuse-eip-quickstart

Step 4 - Add the JBoss Fuse server
admin=redhat,admin update users.properties in /etc first
Run the new server wizard 
Select Red Hat JBoss Fuse 6.x Server
Select installed product under target folder
Enter admin/redhat from above

Step 5 - Start JBoss Fuse server and the shell should display
 
[kpeeples@localhost bin]$ ./fuse Please wait while JBoss Fuse is loading... 100% [=================================================================]
JBoss Fuse (6.0.0.redhat-015) http://www.redhat.com/products/jbossenterprisemiddleware/fuse/
Hit '' for a list of available commands and '[cmd] --help' for help on a specific command. Hit '' or 'osgi:shutdown' to shutdown JBoss Fuse.
JBossFuse:karaf@root>

Step 6 - Import the existing maven project to review the files

Step 7 - Install the Fuse Application Bundle (FAB) 

Run osgi:install -s fab:mvn:org.jboss.fuse.examples/eip/6.0.0.redhat-024
Response should be the Bundle ID

Step 8 - View the OSGi list to make sure the FAB has been created and active
Run osgi:list - l
[ 234] [Active     ] [Created     ] [       ] [   60] fab:mvn:org.jboss.fuse.examples/eip/6.0.0.redhat-024

Step 9 -  As soon as the Camel route has been started, you will see a directory `work/eip/input` in your JBoss Fuse installation.

Step 10 - Copy the file you find in this example's `src/test/data` directory to the newly created `work/eip/input` directory.

Step 11 -  Wait a few moment and you will find multiple files organized by geographical region under `work/eip/output':

** `2012_0003.xml` and `2012_0005.xml` in `work/eip/output/AMER`
** `2012_0020.xml` in `work/eip/output/APAC`
** `2012_0001.xml`, `2012_0002.xml` and `2012_0004.xml` in `work/eip/output/EMEA`

Step 12 -  Use `log:display` on the ESB shell to check out the business logging.

        [main]    Processing orders.xml
        [wiretap]  Archiving orders.xml
        [splitter] Shipping order 2012_0001 to region EMEA
        [splitter] Shipping order 2012_0002 to region EMEA
        [filter]   Order 2012_0002 is an order for more than 100 animals
