## What's new

* **AdGuard Home and Pi-hole as providers.** If you already run one of them as your network's DNS server, ipv6ddns can now write the names of your devices into it and keep their addresses right. Nothing changes on the router or the devices: they keep asking the DNS server they use now.
  * `adguardhome` keeps each name as DNS rewrites, one for each address. Rewrites you disabled, and rewrites whose answer is not an address, such as an alias, are left as they are.
  * `pihole` keeps each name as local DNS records, one for each address. It needs Pi-hole 6 or later. Pi-hole also answers the reverse lookups. Records you wrote with several names on one line are left as they are.
  * Both are tested against the real AdGuard Home and Pi-hole in CI. The settings are in the [providers reference](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/reference/providers.md).
* **The resolver's answers last no longer than their addresses.** An address was answered with the zone's TTL however soon it expired, so a client could keep it after the resolver had dropped it. An answer's TTL is now the zone's, or the time its soonest address has left, whichever is shorter.
* **NixOS:** the module runs the service with the unit the package brings, so the service has the same limits as with the other packages.

## New guides

* [Every device by name, in AdGuard Home](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/adguard-home.md), and [its side for the Home Assistant app](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/home-assistant/adguard-home.md), with the AdGuard Home app on the same machine.
* [Every device by name, in Pi-hole](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/pi-hole.md).
* [A public name for any device, over IPv6](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/public-ipv6-names.md), and [its side for the app](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/guides/home-assistant/public-ipv6-names.md): a name such as `nas.example.com` that follows the device when the ISP changes the IPv6 prefix.

Nothing in the configuration changes.

## Changelog
* 733eeb7 build: the NixOS module runs the service by the packages' own unit
* 2cbc93e ci: the hash of the Go modules, for Nix, is kept by CI itself
* 203e3be feat: the resolver's answers last no longer than their addresses
* bf598a9 test: an ANY answer of a name's addresses has the soonest expiry of both families
* 37fe331 docs: a guide for a public name of any device over IPv6, and its side for the app
* 0fd3c18 test: the expiry the TTL test moves is read by the server's goroutine, atomically
* 4b77470 feat: AdGuard Home and Pi-hole as providers: the names as their rewrites and local DNS records
* 91cfa0c docs: guides for the names in the AdGuard Home or Pi-hole you already run, and the app's side of AdGuard Home's
* b09aa82 docs: how Home Assistant itself uses the AdGuard Home app for the names
* b6d6142 fix(pihole): its errors start in lower case, as Go's do
