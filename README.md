# munin-plugins-syncthing
[Munin](http://munin-monitoring.org/) plugins to monitor [Syncthing](https://syncthing.net/)

## Requirements
* [jq](https://stedolan.github.io/jq/)

## Installation
in order to install this plugin you should copy it to /usr/share/munin/plugins and then create a symbolic link to your /etc/munin/plugins directory.
~~~bash
# cd /etc/munin/plugins
# ln -s /usr/share/munin/plugins/syncthing_system_status_uptime  /etc/munin/plugins
~~~

## Configuration
You need to configure a file in /etc/munin/plugin-conf.d/, it should contain the following variables :
~~~bash
[syncthing_*]

env.ST_APIKEY abcdefgh12345678
env.ST_HOST 127.0.0.1
env.ST_PORT 8384
env.ST_PROTO http
~~~
