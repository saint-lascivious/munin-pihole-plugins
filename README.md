# munin-pihole-plugins

Munin plugins for monitoring [Pi-Hole](https://github.com/pi-hole/pi-hole), a hard fork of [MuninPiholePlugins](https://github.com/Rauks/MuninPiholePlugins)

## Automated Installation
Automated installation script for Debian/Ubuntu derivatives
* Download the munin-pihole-plugins script
```
wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/script/munin-pihole-plugins
```
* Ensure it is executable
```
chmod +x munin-pihole-plugins
```
* Install munin-pihole-plugins
```
./munin-pihole-plugins --install
```
For detailed usage information use
```
./munin-pihole-plugins --help
```

## Manual Installation
* Install Munin
See the instructions in my [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy) repository

* Download any/all desired plugins

Number of domains in blocklist
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_blocked -P /usr/share/munin/plugins
```
Cache information
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_cache -P /usr/share/munin/plugins
```
Number of unique clients currently/ever seen
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_clients -P /usr/share/munin/plugins
```
Forwarded queries and cache hits
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_hits -P /usr/share/munin/plugins
```
Block rate as a percentile
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_percent -P /usr/share/munin/plugins
```
Total queries/blocked queries
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_queries -P /usr/share/munin/plugins
```
Reply type (IP, NXDOMAIN, CNAME, etc.)
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_replies -P /usr/share/munin/plugins
```
Blocking status
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/usr/share/munin/plugins/pihole_status -P /usr/share/munin/plugins
```
Number of unique domains seen
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
sudo ln -s /usr/share/munin/plugins/pihole_cache /etc/munin/plugins/pihole_cache
```
```
sudo ln -s /usr/share/munin/plugins/pihole_clients /etc/munin/plugins/pihole_clients
```
```
sudo ln -s /usr/share/munin/plugins/pihole_hits /etc/munin/plugins/pihole_hits
```
```
sudo ln -s /usr/share/munin/plugins/pihole_percent /etc/munin/plugins/pihole_percent
```
```
sudo ln -s /usr/share/munin/plugins/pihole_queries /etc/munin/plugins/pihole_queries
```
```
sudo ln -s /usr/share/munin/plugins/pihole_replies /etc/munin/plugins/pihole_replies
```
```
sudo ln -s /usr/share/munin/plugins/pihole_status /etc/munin/plugins/pihole_status
```
```
sudo ln -s /usr/share/munin/plugins/pihole_unique /etc/munin/plugins/pihole_unique
```

* Restart Munin services
```
sudo systemctl restart munin munin-node
```

## Configuration

Provided munin-node and Pi-hole exist on the same host, the default configuration should Just Work. If you have a non-standard configuration or Pi-hole is running on a seperate host, you can do one of the following.

* Sample setup for `/etc/munin/plugin-conf.d/pihole`
```
[pihole_*]
    user root
    env.host 127.0.0.1
    env.port 80
    env.api /admin/api.php
    env.cachesuffix ?getCacheInfo&auth=
    env.webpassword PIHOLE_SETUPVARS_WEBPASSWORD_HERE
```

* Download and edit a sample `/etc/munin/plugin-conf.d/unbound` file from this repo:
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/munin-pihole-plugins/master/etc/munin/plugin-conf.d/pihole -P /etc/munin/plugin-conf.d
```
The `env.webpassword` value can be obtained from the Pihole host's `/etc/pihole/setupVars.conf` file. The plugin attempts to obtain this value itself.

## Help! My graphs aren't showing up!

* Be patient

Graphs should be generated at five minute intervals. If you still do not see graphs after this time, try restarting the machine and waiting a further five minutes. If you still can not get any graphs to display, contact me for further support.

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

## Related projects
* [lighttpd-external-munin-proxy](https://github.com/saint-lascivious/lighttpd-external-munin-proxy)

lighttpd external.conf for Munin webserver proxy

* [munin-unbound-plugins](https://github.com/saint-lascivious/munin-unbound-plugins)

Munin monitoring plugins for Unbound

* [Munin](https://github.com/munin-monitoring/munin)

Main repository for munin master / node / plugins

* [Pi-hole](https://github.com/pi-hole/pi-hole)

A black hole for Internet advertisements

* [Unbound](https://github.com/NLnetLabs/unbound)

Unbound is a validating, recursive, caching DNS resolver.
