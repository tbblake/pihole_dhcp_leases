<!-- https://github.com/tbblake/myScripts/tree/main/dhcpPihole -->
# dhcpPihole
This displays your pihole dhcp lease table in an easy to read format.  A lighttpd configuration is included to restrict what gets logged, to reduce SD card wear & tear.  Only tested on a vanilla pihole install on a vanilla raspbian install on a raspberry pi 3b+.

Additional options can be passed to the php script in the URL for html / text / json / csv / raw, date output, filtering to show just a particular mac address, and sorting options:

* sortOrder
  * 0 - ascending
  * 1 - descending
* sortField
  * 1 - mac address
  * 3 - name
  * 4 - expiration
  * 5 - ip
* fmt
  * 0 - html
  * 1 - text
  * 2 - json
  * 3 - csv
  * 4 - raw dhcp.leases file
* macAddress - pass mac address to show just that address in the output
* noDate - supresses date in output
* htmlTable - output html table (deprecated, use fmt flag)
* textTable - output text table (deprecated, use fmt flag)
* jsonTable - output json table (deprecated, use fmt flag)

## Installation

### Pi-Hole installed on bare OS

Copy dhcpLeases.php to /var/www/html, 16-dhcpLeases.conf to /etc/lighttpd/conf-enabled, then restart lighttpd.

Then browse to the script http://your.pihole.ip.here/dhcpLeases.php

## Pi-Hole installed in docker

Use the supplied Dockerfile to extend pihole which includes the lighttpd configuration and php script.  Update your docker run and/or compose file(s).

Then browse to the script http://your.pihole.ip.here/dhcpLeases.php


Tested against:
* Pi-hole v5.18.2
* FTL v5.25.2
* Web Interface v5.21