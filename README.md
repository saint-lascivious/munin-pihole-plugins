# munin-pihole-plugins

Munin plugins for monitoring [Pi-Hole](https://github.com/pi-hole/pi-hole), a hard fork of [MuninPiholePlugins](https://github.com/Rauks/MuninPiholePlugins)

# Related projects
* [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy)

lighttpd external.conf for Munin webserver proxy

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [Pi-hole](https://github.com/pi-hole/pi-hole)

A black hole for Internet advertisements

# Install Munin
* See the instructions in my [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy) repository

# Usage
* Download the plugins
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_blocked -P /usr/share/munin/plugins
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_cache -P /usr/share/munin/plugins
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


* Create the symbolic links
```
sudo ln -s /usr/share/munin/plugins/pihole_blocked /etc/munin/plugins/pihole_blocked
```
```
sudo ln -s /usr/share/munin/plugins/pihole_cache /etc/munin/plugins/pihole_cache
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

Or let "munin-node-configure --shell | bash" do it for you.

# Configuration
* Edit the exiting `plugins.conf` file

Sample setup for '/etc/munin/plugin-conf.d/plugins.conf'
```
[pihole_*]
    user root
    env.host 192.168.1.123
    env.port 80
    env.api /admin/api.php
```

* Or download the example configuration from this repo:
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/etc/munin/plugin-conf.d/plugins.conf -P /etc/munin/plugin-conf.d
```

Note: It's assumed you'll edit the `env.host` value to properly reflect the host.


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
