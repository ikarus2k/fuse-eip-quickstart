fuse-eip-quickstart
===================

Fuse ESB Enterprise Enterprise Integration Patterns Quickstart.  This quickstart will help you easily setup a quickstart using the latest version of JBoss Fuse and JBoss Developer Studio.

Step 1 – View the README in 'installs' directory

Step 2 – Add the JBoss Fuse product from the Red Hat Customer Support Portal or JBoss.org
Login to RHN or jboss.org
https://www.jboss.org/products/fuse.html
https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?downloadType=distributions&product=jboss.fuse&productChanged=yes
update the zip filename in init.sh in the FUSE_BIN variable

Step 3 - Run 'init.sh' & read output
sample posted to init.sh.output under support

Step 4 - Install and/or Setup JBDS for project import
Indicate where to get the JBDS

Step 5 - Add the JBoss Fuse server
admin=redhat,admin update users.properties in /etc first
 
Step 6 - Import the maven project to review the files

Step 7 - Start JBoss Fuse
 
[kpeeples@localhost bin]$ ./fuse Please wait while JBoss Fuse is loading... 100% [=================================================================]
JBoss Fuse (6.0.0.redhat-015) http://www.redhat.com/products/jbossenterprisemiddleware/fuse/
Hit '' for a list of available commands and '[cmd] --help' for help on a specific command. Hit '' or 'osgi:shutdown' to shutdown JBoss Fuse.
JBossFuse:karaf@root>

Step 8 - When the JBoss Fuse console appears, install the Fuse Application Bundle (FAB) 

JBossFuse:karaf@root>osgi:install -s fab:mvn:org.jboss.fuse.examples/eip/6.0.0.redhat-024

show .m2 repo

view the OSGi list to make sure the FAB has been created and active
osgi:list - l
[ 234] [Active     ] [Created     ] [       ] [   60] fab:mvn:org.jboss.fuse.examples/eip/6.0.0.redh
at-024

Step 9 -  As soon as the Camel route has been started, you will see a directory `work/eip/input` in your JBoss Fuse installation.

Step 10 - Copy the file you find in this example's `src/test/data` directory to the newly created `work/eip/input` directory.

Step 11 -  Wait a few moment and you will find multiple files organized by geographical region under
`work/eip/output':

** `2012_0003.xml` and `2012_0005.xml` in `work/eip/output/AMER`
** `2012_0020.xml` in `work/eip/output/APAC`
** `2012_0001.xml`, `2012_0002.xml` and `2012_0004.xml` in `work/eip/output/EMEA`

Step 12 -  Use `log:display` on the ESB shell to check out the business logging.

        [main]    Processing orders.xml
        [wiretap]  Archiving orders.xml
        [splitter] Shipping order 2012_0001 to region EMEA
        [splitter] Shipping order 2012_0002 to region EMEA
        [filter]   Order 2012_0002 is an order for more than 100 animals

References:



