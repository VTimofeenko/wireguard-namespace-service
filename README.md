# WireGuard-namespace-service
A script and a systemd service that creates isolated network namespace with traffic routed through WireGuard interface.

Usage example with [firejail](https://firejail.wordpress.com/):

```
(user) $ curl ifconfig.co
X.X.X.X
(root) # MY_IP="10.8.0.2" wg_namespace_cli up wg0
(user) $ firejail --noprofile --netns=wg0 sh
sh-5.1$ curl ifconfig.co
Y.Y.Y.Y
```

This allows to create sandboxes the traffic of which will be routed the WireGuard interface.

# Installation

TODO

# Setup

Setup WireGuard configuration file in `/etc/wireguard/wg0.conf` ([debian manpages link](https://manpages.debian.org/unstable/wireguard-tools/wg.8.en.html#CONFIGURATION_FILE_FORMAT))


# Customizing

TODO

# Reference

* [WireGuard Routing & Network Namespace Integration](https://www.wireguard.com/netns/)
