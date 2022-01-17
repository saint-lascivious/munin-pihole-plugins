# munin-pihole-plugins

Munin plugins for monitoring [Pi-Hole](https://github.com/pi-hole/pi-hole), a hard fork of [MuninPiholePlugins](https://github.com/Rauks/MuninPiholePlugins)

## Related projects
* [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy)

lighttpd external.conf for Munin webserver proxy

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [Pi-hole](https://github.com/pi-hole/pi-hole)

A black hole for Internet advertisements

## Install Munin
* See the instructions in my [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy) repository

## Usage
* Download the plugins
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_blocked -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_blockrate -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_cache -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_cache_info -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_clients -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_queries -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_reply -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_unique -P /usr/share/munin/plugins
```


* Ensure they're executable
```
sudo chmod a+x /usr/share/munin/plugins/pihole_*
```


* Create symbolic links
```
sudo ln -s /usr/share/munin/plugins/pihole_blocked /etc/munin/plugins/pihole_blocked
```
```
sudo ln -s /usr/share/munin/plugins/pihole_blockrate /etc/munin/plugins/pihole_blockrate
```
```
sudo ln -s /usr/share/munin/plugins/pihole_cache /etc/munin/plugins/pihole_cache
```
```
sudo ln -s /usr/share/munin/plugins/pihole_cache_info /etc/munin/plugins/pihole_cache_info
```
```
sudo ln -s /usr/share/munin/plugins/pihole_clients /etc/munin/plugins/pihole_clients
```
```
sudo ln -s /usr/share/munin/plugins/pihole_queries /etc/munin/plugins/pihole_queries
```
```
sudo ln -s /usr/share/munin/plugins/pihole_reply /etc/munin/plugins/pihole_reply
```
```
sudo ln -s /usr/share/munin/plugins/pihole_unique /etc/munin/plugins/pihole_unique
```

## Configuration

Provided munin-node and Pi-hole exist on the same host, the default configuration should Just Work. If you have a non-standard configuration or Pi-hole is running on a seperate host, you can do one of the following.

* Edit the existing `plugins.conf` file

Sample setup for `/etc/munin/plugin-conf.d/plugins.conf`
```
[pihole_*]
    user root
    env.host 127.0.0.1
    env.port 80
    env.api /admin/api.php
    env.cachesuffix ?getCacheInfo&auth=
    env.webpassword PIHOLE_SETUPVARS_WEBPASSWORD_HERE
```

* Download and edit a sample `plugins.conf` file from this repo:
```
wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/etc/munin/plugin-conf.d/plugins.conf -q -O - | sudo tee /etc/munin/plugin-conf.d/plugins.conf
```
The `env.webpassword` value can be obtained from the Pihole host's `/etc/pihole/setupVars.conf` file. The plugin attempts to obtain this value itself.

## Contact
* Discord
[SaintLascivious](https://discord.gg/NC7taVyn)

* Email
saint@sainternet.xyz

* IRC
[##saint-lascivious](https://webchat.freenode.net/##saint-lascivious)

* Reddit
[saint-lascivious](https://www.reddit.com/user/saint-lascivious)

![alt text][logo]

[logo]:https://vignette.wikia.nocookie.net/pokemon/images/7/76/265Wurmple.png "Using the spikes on its rear end, Wurmple peels the bark off trees and feeds on the sap that oozes out. This Pokémon's feet are tipped with suction pads that allow it to cling to glass without slipping."
