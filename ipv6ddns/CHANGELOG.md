## What's new

* **Encrypted DNS for your clients.** A resolver answers over DNS over TLS (`tls://`, port 853), DNS over HTTPS (`https://`, port 443, at `/dns-query`) and DNS over QUIC (`quic://`, UDP port 853), as entries of its `listen` beside the plain ones. Phones, computers and browsers can then use it as their private DNS: Android's Private DNS, iOS and macOS profiles, Windows 11, Firefox and Chrome. See [encrypted DNS for the clients](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/resolver.md#encrypted-dns-for-the-clients).
* **Certificates from Let's Encrypt.** ipv6ddns gets the certificate itself, and renews it, by the DNS challenge: it writes the TXT record through a credential of your public zone, of `cloudflare`, `route53`, `rfc2136` or `duckdns`. The name needs no address on the internet. Or give the files of a certificate you get otherwise, which are read again when they change, without a restart.
* **Certificates are named, under `certificates`,** and a resolver or the web server gives one as its `tls`. Several servers can show one certificate, which is got and renewed once for all of them. The report has a `Certificates:` section with each one, the servers that show it, and until when, in amber two weeks before it ends.
* **The web server over HTTPS,** with `https://` entries in `webserver.listen`, port 8443 by default, and `webserver.tls`. The plain entries stay HTTP, as the Home Assistant app's page needs.
* **A push source: your router sends its addresses, as to a DynDNS service.** `type: push` takes the dyndns2 protocol at `/nic/update` of the web server, which most routers can send to as a custom provider: UniFi gateways, Fritz!Box, OPNsense, pfSense and OpenWrt. A task with the source gives a name the router's public addresses as soon as they change, without asking the internet. See [a router's updates](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/sources.md#a-routers-updates).
* **A Fritz!Box's prefix of the LAN, with `ip.prefix_source`.** A Fritz!Box also sends the IPv6 prefix of its LAN. A filter with `prefix_source` takes only the IPv6 addresses in it, so when the ISP changes the prefix, the addresses of the old one leave the names as soon as the router sends the new one, rather than an hour later.

New in the configuration, and nothing in it changes: `certificates`, the `tls` of resolvers and of `webserver`, the `tls://`, `https://` and `quic://` entries of a resolver's `listen` and the `https://` ones of the web server's, `type: push` sources, and `ip.prefix_source`.

Encrypted DNS, Let's Encrypt and the push source are tested in CI against real clients and servers: kdig and dig, Let's Encrypt's own test authority, Pebble, with BIND, and inadyn, ddclient and curl as a router's clients. They are not yet tested with phones, Let's Encrypt itself, or the routers' own interfaces: reports of how they work with yours are welcome.

## Changelog
* 047f3380d78a94151541d3b1648b1951c24fe49e build: the hash of the Go modules, for Nix
* c809a830c4e19699b6519fd0c51ddb49f680e458 build: the hash of the Go modules, for Nix
* 3133890792ac8e0bc5e6b9432e6467686517c097 feat: a push source, of the addresses a router sends as to a DynDNS service
* cb6042a83684f04dcfa30bf057917610388448ad feat: certificates, by name, which the resolvers and the web server give as their tls: one, of one manager, for several servers; and a certificate whose key isn't its own is got again
* 5434d9611b404ba257ab41add7d4c17f8c98e43d feat: the prefix of the LAN a Fritz!Box pushes, and ip.prefix_source, which takes the IPv6 addresses in it alone
* 32f6a807a92ec9027acdd7215377faf3a3444d6a feat: the resolver answers over DNS over TLS, HTTPS and QUIC
* 3bf6e30a1656a19f6e69dbe0875fed6b21d4050c feat: the resolver's certificate from Let's Encrypt, by the DNS challenge, with tls.acme
* fa5a009b85a72ffe50cfd2bd92ba4ac4132f44f7 feat: the resolver's certificate is a tls block, its files relative to the configuration's folder
* ed8be2ade3839a60048e741d46fcced28a1ec91e feat: the web server over HTTPS, with https:// entries of webserver.listen and webserver.tls, files or acme, as a resolver's
* 6e66581ef695b285e3bdf3f380e5d5771559f4e2 fix(resolver): no upstream server is an error, not an answer of nothing; a DNS over QUIC stream that ends before its message is reset both ways; a certificate's status has names of its own
* 0a4c5e615275b57bf5ab31f189e49ee849c15fa4 fix(resolver): the encrypted transports say why they leave an error unchecked; the live test's dig doesn't check the certificate, which kdig does
* b6c90417d7a2e95581fd6427d57d94e646d5d44b refactor: the push sources' prefixes, a snapshot of each round of matching, not a function in the configuration; a push at a time, and the prefix for the source's lifetime; the web server's parts served alike


