## What's new

* **A provider for any DNS server that takes dynamic updates (RFC 2136)**, such as BIND, Knot and PowerDNS, and Windows DNS where it allows nonsecure updates. Each update replaces the name's A and AAAA records in one step, over TCP, signed with a TSIG key when you give one, and leaves the name's other records. It is tested against BIND in CI. Give ipv6ddns a zone of its own, not one a DHCP server registers its clients in. The settings are in the [providers reference](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/reference/providers.md#rfc2136).
* **An address that another device takes leaves the old device's names at once.** Before, it stayed at the device it left until its lifetime ended, an hour by default. So the old name could give the address of another device, and the new device had no name meanwhile. This happens when a device replaces another, a container is made again with a new MAC, or DHCP hands a freed address to another device. Now the newest sighting on the link wins. Two devices given the same address make it move back and forth, and the log warns of it. This comes with [ipv6disc v0.25.0](https://github.com/miguelangel-nubla/ipv6disc/releases/tag/v0.25.0).
* **The report counts `1 host` and `1 address`**, from ipv6disc.
* **The README shows a report where everything works.**

Nothing in the configuration changes.

## Changelog
* 1f56f64 build: ipv6disc v0.25.0
* ed8776d docs: an address another device takes leaves the old device's names at once, with its test
* e50ca07 feat: an rfc2136 provider, for any DNS server that takes dynamic updates, as BIND does
* 2a69a5b build: the hash of the Go modules, for Nix
* 26032d5 ci: the macOS tests run on main, weekly and by hand, not at every commit of dev
* 921d35f docs: the README's report is of a setup where everything works
