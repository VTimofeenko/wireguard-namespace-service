# WireGuard-namespace-service
A script and a systemd service that creates isolated network namespace with traffic routed through WireGuard interface.

This allows to create sandboxes the traffic of which will be routed the WireGuard interface.

The script is written in bash and can be used separately from the service.

Script usage example with [firejail](https://firejail.wordpress.com/):

```
(user) $ curl ifconfig.co
X.X.X.X
(root) # MY_IP="10.8.0.2" wg_namespace_cli up wg0
(user) $ firejail --noprofile --netns=wg0 sh
sh-5.1$ curl ifconfig.co
Y.Y.Y.Y
```

Systemd service can be run as

```
(root) # systemctl start wg-netnamespace@wg0
```

Where wg0 is the name of the config file in `/etc/wireguard`


# Installation

TODO

# Setup

* Setup WireGuard configuration file in `/etc/wireguard/wg0.conf` ([debian manpages link](https://manpages.debian.org/unstable/wireguard-tools/wg.8.en.html#CONFIGURATION_FILE_FORMAT))
* If using systemd service – create a service drop-in and specify the IP for the interface. E.g.:

    ```
    (root) # systemd edit wg-netnamespace@wg0
    [Service]
    Environment=MY_IP=10.8.1.101
    ```

# Customizing

TODO

# Reference

* [WireGuard Routing & Network Namespace Integration](https://www.wireguard.com/netns/)
