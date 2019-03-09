
=========================================================
Tom's memory monitor updated to v3
(based on Matthew Wall's mem demonstration extension)
 - vinceskahan@gmail.com 2014-1129
=========================================================

# update 2019-0308: this requires python3

This example illustrates how to implement a service and package it so that it
can be installed by the extension installer.  The mem service collects memory
usage information about a single process then saves it in its own database.
Data are then displayed using standard weewx reporting and plotting utilities.

Installation instructions:

1) run the installer:

setup.py install --extension extensions/mem

2) restart weewx:

sudo /etc/init.d/weewx stop
sudo /etc/init.d/weewx start

This will result in a skin called mem with a single web page that illustrates
how to use the monitoring data.  See comments in mem.py for customization
options.


Notes:
  1. the 'first' time the skin attempts to generate pages you may see a 
       syslog entry saying 
          "cheetahgenerator: skipping report {'template': 'index.html.tmpl'}: 
               cannot find start time"
     - what is happening is the skin is being processed before the initial
       mem.sdb databased has been seeded with data.  The message goes away
       before the 'second' time the skin is processed.
  2. see bin/user/mem.py for more commentary


