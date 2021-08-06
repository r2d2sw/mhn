Modern Honey Network
====================

MHN is a centralized server for management and data collection of honeypots. MHN
allows you to deploy sensors quickly and to collect data immediately, viewable
from a neat web interface. Honeypot deploy scripts include several common
honeypot technologies, including [Snort](https://snort.org/),
[Cowrie](http://www.micheloosterhof.com/cowrie/),
[Dionaea](https://www.edgis-security.org/single-post/dionaea-malware-honeypot), and
[glastopf](https://github.com/glastopf/), among others.

## Features

MHN is a Flask application that exposes an HTTP API that honeypots can use to:
- Download a deploy script
- Connect and register
- Download snort rules
- Send intrusion detection logs

It also allows system administrators to:
- View a list of new attacks
- Manage snort rules: enable, disable, download


## Installation

- The MHN server is supported on Ubuntu 18.04, Ubuntu 16.04, and Centos 6.9.  
- Other versions of Linux may work but are generally not tested or supported.

Install Git

    # on Debian or Ubuntu
    $ sudo apt install git -y
    
Install MHN
    
    $ cd /opt/
    $ sudo git clone https://github.com/r2d2sw/mhn.git
    $ cd mhn/

Run the following script to complete the installation.  While this script runs,
you will be prompted for some configuration options.  See below for how this
looks.

    $ sudo ./install.sh


### Configuration
    
    ===========================================================
    MHN Configuration
    ===========================================================
    Do you wish to run in Debug mode?: y/n n
    Superuser email: YOUR_EMAIL@YOURSITE.COM
    Superuser password: 
    Server base url ["http://1.2.3.4"]: 
    Honeymap url ["http://1.2.3.4:3000"]:
    Mail server address ["localhost"]: 
    Mail server port [25]: 
    Use TLS for email?: y/n n
    Use SSL for email?: y/n n
    Mail server username [""]: 
    Mail server password [""]: 
    Mail default sender [""]: 
    Path for log file ["mhn.log"]: 


### Running

If the installation scripts ran successfully, you should have a number of
services running on your MHN server.  See below for checking these.

    user@precise64:/opt/mhn/scripts$ sudo /etc/init.d/nginx status
     * nginx is running
    user@precise64:/opt/mhn/scripts$ sudo /etc/init.d/supervisor status
     is running
    user@precise64:/opt/mhn/scripts$ sudo supervisorctl status
    geoloc                           RUNNING    pid 31443, uptime 0:00:12
    honeymap                         RUNNING    pid 30826, uptime 0:08:54
    hpfeeds-broker                   RUNNING    pid 10089, uptime 0:36:42
    mhn-celery-beat                  RUNNING    pid 29909, uptime 0:18:41
    mhn-celery-worker                RUNNING    pid 29910, uptime 0:18:41
    mhn-collector                    RUNNING    pid 7872,  uptime 0:18:41
    mhn-uwsgi                        RUNNING    pid 29911, uptime 0:18:41
    mnemosyne                        RUNNING    pid 28173, uptime 0:30:08


## Support or Contact
MHN is an open source project that relies on community involvement. Please check out our troubleshooting guide on the wiki. We will also lend a
hand, if needed. Find us at: <modern-honey-network@googlegroups.com>.

### Credit and Thanks
MHN was originally created by Anomali, Inc.

MHN leverages and extends upon several awesome projects by the Honeynet project.
Please show them your support by way of donation.

Forked from https://github.com/pwnlandia/mhn

## LICENSE

Modern Honeypot Network

This program free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
