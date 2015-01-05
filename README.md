https://walleminnovativesolutions.atlassian.net/browse/TPSBF-781 
Similar to the old Jira (I don't remember #), there are 04 parts to do:

1) App-Support will send a small module to vessel and ask Master to run it (on Windows machine). This module will scan Vessel's network and export it to the txt file (or maybe a zip file?). We will ask Master to send this file back to us.

2) After received the result file sent from Master, App-Support will check the current network on the Vessel.

3) App-Support will notify Master/Vessel to not use a specific IP.

4) IP (from step 3) will be manual configured on the Marinebox as a new sub interface.
Add a new sub interface to Marinebox, steps:
   4.1) run command `sudo nano /etc/network/interfaces`
   4.2) append text
          auto eth0:0 # this value is up to each Vessel's network. step #2
          iface eth0:0 inet static
            address 192.168.1.123 # this value is up to each Vessel's network, free IP only
            netmask 255.255.255.0 # this value is up to each Vessel's network.
   4.3) ctrl +X
   4.4) run command: `sudo /etc/init.d/networking restart`
   4.5) run command: `ip addr` to check change. Done.


Final result:
Marinebox will always have a sub interface before delivering to Vessel.

== This is part 1 ==
