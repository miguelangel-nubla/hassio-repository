## What's new

v0.31.0 was tagged, but never published: its release stopped at a test of DNS over QUIC's shutdown, which a change of that version made fail now and then. This is that release, with the fix, so the notes are of everything since v0.30.0, and the changelog below has the fix alone: all the commits are in [v0.30.0...v0.31.1](https://github.com/miguelangel-nubla/ipv6ddns/compare/v0.30.0...v0.31.1).

This release comes from a review of the whole project. It is mostly fixes, and a configuration that loaded before may now be refused at the start, with an error that says what to write: see *What changes in the configuration*, below.

* **Builds for routers without a floating point unit.** MIPS was built for a processor with one, and OpenWrt's MIPS routers have none, so the binary stopped with `Illegal instruction`. `mips`, `mipsle`, `mips64` and `mips64le` are built without one now, and still run on a MIPS that has it. A new `armv5` build is for ARM without one, as the Broadcom routers of Asuswrt-Merlin, where `armv6` and `armv7` stop. The [installation page](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/installation.md#getting-it) says which one a router takes. They were checked under emulation of such processors, not on a real router yet: reports are welcome. `js/wasm`, which could never run, is no longer built.
* **A `tls_fingerprint` pins the certificate in every provider.** AdGuard Home, OPNsense, pfSense, Pi-hole, Technitium and UniFi accepted any certificate the system verifies, beside the one of the fingerprint. With a fingerprint, only that certificate is accepted now, as MikroTik's provider and the discovery plugins already had it. Without one, the system must verify the certificate, and the error gives its fingerprint.
* **A resolver that listens on a port alone, as `dns://53`, answers its IPv4 clients by default.** Its default `allow` took the networks of IPv6 alone, so every IPv4 client was refused.
* **A configuration error no longer restarts the service every 5 seconds.** It ends with the exit code 78, which the systemd unit doesn't restart: the error stays in the log until you fix it and restart the service. OpenRC still restarts it. Any other failure is restarted as before. A web server's port that another program holds now stops the start before the resolvers listen or Home Assistant is told of the device.
* **The files ipv6ddns keeps are synced to the disk before they replace the old ones:** the push file, the challenges' and names' files, the Home Assistant device's key, and ACME's certificates and keys. Before, a power cut could leave one empty, and the start then stopped at it, or Home Assistant no longer knew the device.
* **The `state_dir` the documentation gives, `/var/lib/ipv6ddns`, is writable under systemd**, and the NixOS module keeps its state there rather than beside its configuration, in the store. Under OpenRC, the service is no longer given up on after ten crashes.
* **The web report, `/status.json` and `/metrics` hide more:** the path of a DNS over HTTPS upstream, which names the account at NextDNS and others; a provider's or an authority's errors; and the user and query of the ACME directory's URL and of a credential's endpoint. The console's report, and the log, still have them whole. A blocklist's download no longer logs its URL whole.
* **Templates and updates.** A template's name removed while its removal was waiting kept its records at the provider for good. At Route 53, a template's name was made twice, and the removal of one emptied the records of a host that was there. "Update now" just after a start sent an update with no address for each name. A slow update made one call to the provider for each change that came meanwhile.
* **Pushed addresses keep their own lifetime across a restart**, which renewed the ones the router didn't send again. A push without `myip` refuses an address of a carrier's NAT or a tunnel, as it does one of the LAN.
* **The resolver.** EDNS is the resolver's own on each side, and no longer passed through. The cache no longer serves an answer to a query without RD to one with it. A DNS over QUIC answer over 65535 bytes, and a DNS over TLS connection gone silent, no longer cost the query. Names under a wildcard, and the empty names of a private reverse zone, get the right answer.
* **Blocklists.** A captive portal's page, or a server's error page, no longer replaces a list, an empty copy is downloaded again, and a byte order mark is read.
* **Providers.** RFC 2136 can empty a name under a wildcard, and takes a `tsig_key` written with capitals. OVH tries a failed zone refresh again. OVH and Porkbun no longer take a record of another name that a listing gives, and they, OPNsense and pfSense match a name whatever its case.
* **Home Assistant.** When the device's key changes, or is forgotten, the connections of the old key are closed; Home Assistant connects again with the new one.
* **`$$${NAME}` is a `$` before the value** of the variable. `$${` is a literal `${` as before.
* **New in the documentation:** what goes through `HTTPS_PROXY`, and what connects directly, in [Proxies](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/configuration.md#proxies); and the manual page's exit codes.

## What changes in the configuration

Refused at the start now, with an error that names the setting and what to write:

* **An `allow` given empty**, as `allow: ${ALLOWED}` with the variable unset, which gave the default: everyone, for a web server. Leave `allow` out for the default.
* **A `ttl` that isn't whole seconds**, for every provider, and Cloudflare's `ttl: 0s`: write `1s` for Cloudflare's automatic TTL.
* **A `tls_fingerprint` beside an `http://` address.**
* A source's setting of another type of source, as `addresses` in an `http` source, which was ignored.
* A web server with no `http://` or `https://` entry, and two web servers on one address and port.
* A push source's name with a comma, a slash or a space around it, or `.` and `..`; two push sources of one file; a push `lifetime` under `1s`.
* An `acme.directory` that isn't an `http://` or `https://` URL; under ACME, a certificate and a key of one file, or of the account key's.
* Two blocklists whose names differ by case alone.
* An unquoted `y`, `n`, `yes`, `no`, `on` or `off` as a name, which YAML read as true or false: quote it.

Accepted as before, but doing something else:

* **A `tls_fingerprint` in an HTTP provider** accepts that certificate alone. If the server's certificate is one a public authority signs and it is renewed, the fingerprint must be renewed too, or removed to have the system verify it.
* **`$$${NAME}`** gives a `$` and the value, where it gave `$${NAME}`.

## Changelog
* 774c82bc4d1a9a6bf4b273abea97fb0404ba8279 fix(resolver): a connection of DNS over QUIC accepted just before Shutdown is closed while its socket is open


