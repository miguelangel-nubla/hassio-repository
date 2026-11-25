## What's new

* **UniFi, as a DNS provider and as a discovery plugin.** ipv6ddns talks to the UniFi Network API of a UniFi OS console (UDM, UDR, UCG, UXG), of UniFi OS Server, or of a self-hosted UniFi Network Application, with an API key or a local user. See [UniFi](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/unifi.md).
  * **The `unifi` provider** keeps the names as the gateway's local DNS records, its *DNS Records*, one for each address, which every device that uses the gateway as its DNS server gets. A record you disabled, or of another type, is left as it is. UniFi Network 8.2.93 or later.
  * **The `unifi` discovery plugin** reads the clients the gateway has connected now, UniFi's own devices included: their IPv4 address, their IPv6 addresses where UniFi has them, the host name they gave, and the name you gave them in UniFi. It comes with [ipv6disc v0.26.0](https://github.com/miguelangel-nubla/ipv6disc/releases/tag/v0.26.0).
  * Both are tested live, in CI, against a self-hosted Network Application and against UniFi OS Server, which have no gateway: what a real gateway serves and lists, IPv6 included, is not tested yet. Reports of how it works with yours are welcome.
* **Technitium: a disabled record of an address the name has is enabled.** Technitium enables a name's disabled records of a type only when a record of that type is added, so a name whose only address had a disabled record stayed unanswered. Now that record is enabled, and one of an address the name no longer has is removed, as [the docs](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/configuration.md#disabled-records) say.
* **A picture of what ipv6ddns does**, atop the README: it finds the devices on the network and keeps a DNS name pointing at each, on the LAN and on the internet, IPv6 and IPv4.
* **New pages:** a [multi-WAN guide](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/multi-wan.md), of a public name on a network with several ISPs, with what fails over by itself and what the router must do; and pages of the platforms ipv6ddns both reads and writes: [UniFi](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/unifi.md), [OpenWrt](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/openwrt.md), [OPNsense](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/opnsense.md) and [pfSense](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/pfsense.md).

New in the configuration, and nothing in it changes: the `unifi` provider, and the `unifi` type of discovery plugin.

## Changelog
* b61e52881e4cecd610b19180cf8e279ccf822e3a build: the hash of the Go modules, for Nix
* 2d9d1de1cc8fa7fb9f46b0d52b0f5d83443356a8 build: the hash of the Go modules, for Nix
* 94b1b8637297362e0a0090233d11278ed78a9454 feat: a unifi provider, of a UniFi gateway's local DNS records: UniFi OS with an API key or a user, or a self-hosted Network Application with a user; tested live against both
* a5dfa0bc7a13910d60d0e60181fb0b8bf2a221bb feat: ipv6disc v0.26.0, and its unifi discovery plugin: the clients a UniFi gateway has connected, with their addresses and names
* 73dedbc538a73b823126985aefe656edda31c02d fix(technitium): a disabled record of an address the name has is enabled: Technitium enables one only when a record of its type is added, so with nothing added it stayed disabled and unanswered
* 2b13d469d8f1f4d8210d5322f72521915a96eada refactor: the unifi provider uses ipv6disc's UniFi Network client, v0.27.0, as its plugin does: one login, session and errors of both


