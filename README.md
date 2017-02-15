# munin-plugins-syncthing
[Munin](http://munin-monitoring.org/) plugins to monitor [Syncthing](https://github.com/syncthing/syncthing/releases/) and [Syncthing relay](https://github.com/syncthing/relaysrv/releases). 

## Requirements
* [jq](https://stedolan.github.io/jq/)
* Munin already setup and running
* Syncthing already setup and running
* Munin relay setup and running

## Available plugins
~~~bash
# Syncthing
syncthing_system_connections_transfer # graph the total in/out bits 
syncthing_system_status_cpu           # graph the cpu percentage used
syncthing_system_status_gor           # graph the number of go routines used
syncthing_system_status_mem           # graph the amount of memory allocated and obtained from the system
syncthing_system_status_uptime        # graph the uptime
~~~
~~~bash
# Syncthing relay server
strelaysrv_status_gor                 # graph the number of go routines used
strelaysrv_status_num                 # graph the stats provided by the relay
strelaysrv_status_transfer            # graph the relay transfer rate of the last 5 mins
strelaysrv_status_uptime              # graph the relay uptime
~~~

## Installation
Like all munin plugins, you have to create a symbolic link in your Munin plugin directory (usually it is /etc/munin/plugins).
For example suppose you have downloaded the plugins in /usr/share/munin/plugins (with the default ones provided by Munin) you should run the following commands.

~~~bash
# installation of the uptime plugin
# cd /usr/share/munin/plugins && git clone https://github.com/daftaupe/munin-plugins-syncthing.git
# cd /etc/munin/plugins && ln -s /usr/share/munin/plugins/munin-plugins-syncthing/syncthing_system_status_uptime
~~~

## Configuration
Create /etc/munin/plugin-conf.d/syncthing.
Modify the following to fit your Syncthing instance.

~~~bash
# Syncthing
[syncthing_*]

env.ST_APIKEY abcdefgh12345678
env.ST_HOST 127.0.0.1
env.ST_PORT 8384
env.ST_PROTO http
~~~
The APKIKEY is found in the configuration panel of Syncthing web interface. 

Create /etc/munin/plugin-conf.d/strelaysrv. Adapt it to your own case.
~~~bash
#Syncthing relay
[strelaysrv_*]

env.STR_HOST 1.2.3.4
env.STR_PORT 22070
~~~
The APIKEY is not needed for the Syncthing relay monitoring, the /status is publicly available.
You can enable it with the -status-srv flag when starting strelaysrv.

## Preview
![cpu](https://cloud.githubusercontent.com/assets/22810624/22884513/95fb62e6-f1f5-11e6-8215-f7e601ba92dd.png)
![go](https://cloud.githubusercontent.com/assets/22810624/22884515/95fcb7cc-f1f5-11e6-913e-93761d4e0e05.png)
![mem](https://cloud.githubusercontent.com/assets/22810624/22884514/95fb77c2-f1f5-11e6-9d99-352a47bf102b.png)
![transf](https://cloud.githubusercontent.com/assets/22810624/22884512/95f9cde6-f1f5-11e6-892c-d98c079e57d0.png)
![up](https://cloud.githubusercontent.com/assets/22810624/22884511/95f92d5a-f1f5-11e6-9bcc-2c89a7aee4c4.png)
