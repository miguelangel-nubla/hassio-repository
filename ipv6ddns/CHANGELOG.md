## Breaking changes
* 5005bec2e7d21e037a5c587c8f418b18520f5300 feat(homeassistant)!: the key is given, or its provisioning asked for: key_provisioning
* a54534a95b806f35eacc341b3dafd4fc22ebda28 feat(homeassistant)!: where the device listens is given: listen has no default
* 8e621c078573fda5f80f5e2b5affd5651805bdb6 feat(webserver)!: an entry without a port is at 8053, not 80
* 338743bf7db7bc417fe0fc3f2e594c4016be172a feat!: discovery is configured as ipv6disc's, and three flags are left
* 24496c32c56ee5ee3be28d6d633f1ce9fbeac7a6 feat!: filters by how an address was seen: ip.seen and ip.not_seen
* c3f02eaed0e6e278d7ed88fd6eaf40036862dd59 feat!: the discovery's new defaults; filters that take nothing are errors
* f867d6cda800f660a454af1bf0f54b428cb6987b feat(resolver)!: private reverse queries end at the resolver; forward_unknown_private_reverse_queries
* 74e5afcb0360bf9814ece5f4448087c0ae4e6b92 feat(config)!: mask in place of suffix, and nothing kept from before

## Changelog
* 0defc4dee69ff8a54e96acfb0e4392197c15a17f fix(ddns): updates that end, that apply whole, and the providers as the real servers are
* 9834f46fdb94ef4c0a0cd77048caeb3ae1c99f99 fix(source,listen): a run's time is shared, a command's children end with it, and an address listens on its family
* 4be46fe0573797835ffe1c6602ae197d2ea37b17 fix(config): a mask that can't be read is an error, and so are a key given twice and a retry of no time
* 3ad2e8f78b1978ab48d87471a7565d87c86a2cdc fix: the retry is above the debounce, one update at a time at an endpoint, and a Home Assistant client can't hold the device
* 2e8a894bc6dfecf6bffc8000f1cae5549d429bfd ci: the live tests and the providers' run, the generated client is checked, and every platform builds
* 565e2758507bbee1cbc9ef88140842023c23e4a0 fix(homeassistant): a second instance is not the first's device over again
* 5005bec2e7d21e037a5c587c8f418b18520f5300 feat(homeassistant)!: the key is given, or its provisioning asked for: key_provisioning
* a54534a95b806f35eacc341b3dafd4fc22ebda28 feat(homeassistant)!: where the device listens is given: listen has no default
* 8e621c078573fda5f80f5e2b5affd5651805bdb6 feat(webserver)!: an entry without a port is at 8053, not 80
* f4f03d93d9395ef667e12026530774125ebd34df ci: prereleases from dev, which nobody gets who didn't ask for one
* d2a61b81b012ad636a9aef0b5f5c0eefda6e4d4a feat(resolver): ipv6ddns answers DNS itself, and forwards the rest
* cd346c6143700149a9fdc8e9a8cece3373a695a6 feat(resolver): an upstream by host name, found by bootstrap servers of its own
* f6eee843c398976d9bf2bddfecc8b369cff76db4 feat(resolver): upstreams over TLS and HTTPS, a cache, and the names of its addresses
* aa2ff77cac43d647b5267749ff9cee617be095e4 fix(openwrt): a line of uci with one quote, or of no section, is no domain
* 338743bf7db7bc417fe0fc3f2e594c4016be172a feat!: discovery is configured as ipv6disc's, and three flags are left
* c3c69ee222090e4fbb15f80a13111eb4a2831000 style: YAML is written in block style, a key or an item to a line
* 8e5b6194876ca6f64c0718c793433e1849af184a feat: a name for each host, by what it is called: {hostname}, {n} and {mac}
* e400236d04b6991c7ed84b3fa8cf4e06b732a015 build: ipv6disc as its dev branch has it
* 2217c90add4c0bf323e26005671402080d90a72e fix(resolver): a query that comes back is no answer; and tests of what use finds
* 6afa86bce60e67c539ef251156de8a1ee218e22b build: ipv6disc v0.19.0
* 24496c32c56ee5ee3be28d6d633f1ce9fbeac7a6 feat!: filters by how an address was seen: ip.seen and ip.not_seen
* c3f02eaed0e6e278d7ed88fd6eaf40036862dd59 feat!: the discovery's new defaults; filters that take nothing are errors
* 364b249e8b86b64d4cf05e6aaf2d02869254e55f build: ipv6disc v0.20.0
* 88efc988cf91a42b4297a576a63613dc37b17c74 feat(resolver): the reverse of the private networks, answered as RFC 6303 asks
* f867d6cda800f660a454af1bf0f54b428cb6987b feat(resolver)!: private reverse queries end at the resolver; forward_unknown_private_reverse_queries
* ea7b2ab66d9c9eb7ab83d415b978a353dbaa56ba feat: the page lined up, with every lifetime, and why a name waits
* 4e868807cdea3d640737e6213485e947bf560692 build: ipv6disc v0.21.0
* 2872dad76e928010afec2ee24d5987e53b77b16a ci: the build beside the tests, of six platforms; every one weekly
* fe20568d9f01d27b9e628bcefd481ca8e0325ab5 fix(ddns): OPNsense and pfSense apply what an update that failed left unapplied
* c9581cf2b6f44871547c1920f94ed54cd7037993 fix(ddns): Mikrotik and Gravity remove the duplicates of an address
* d710af225eed0d04fa0c830c22eb030790991760 fix(resolver): the status doesn't wait for the bootstrap servers
* 2248c7ef571bf0af308ad45dfb839addfdc1e1c0 fix(windows): the commands of a local update have its timeout together
* c88585ee63f03ef4fa93125718d4ad3d2a36a6de fix(gravity): the requests of an update have updateTimeout together
* d0ecc2278ac300de637e1be3f7949614ddd5fa6f refactor(ddns): one request of each HTTP provider's API, and errors wrapped
* 61c07fd2fa461bf509a250eed7a059cf6bedaf4a Revert "refactor(ddns): one request of each HTTP provider's API, and errors wrapped"
* f5086576f44624e17158988ad8f1545b1030b989 fix(ddns): the providers' errors wrap their cause
* 74fcc482f2454c9cc33eee961ae8fa123e739bb6 feat(ddns): a disabled record of Mikrotik or OPNsense is left as it is
* d3d5281a764d7dfe267987e6e64f5d71386bbd31 fix(technitium): an error tells the HTTP status, and the API's
* 74e5afcb0360bf9814ece5f4448087c0ae4e6b92 feat(config)!: mask in place of suffix, and nothing kept from before
* 6b092d00021eb94feea3bd659f132dfdb0223b10 fix(filter): an IPv4-mapped address is in an IPv4 prefix
* 04815f8e3c99b22a80741fd866c4d7a61c9c155c ci(dependabot): the updates go to dev
* 3f6ab74e791d345d744a4dea29d4c6a2320c59af fix(route53): the start warns of a name written two ways
* f4af1790d3b961863dbcbb1dbad9e4a7e1c0f666 ci: golangci-lint, as ipv6disc's; a deadline that can't be set ends its connection
* 477b8b2802087d21123a6b612636c8235953ad03 ci: the release can be run by hand, on a tag
* c42028a9be860b7e4ff6bdf8b18a7dce45e962d4 build: ipv6disc v0.22.1
* d6ebae00a5f7b103c0131dec44493739608ad619 fix: the errors and warnings in plain words
* 8203f098dcecafc8103205fc7d4410c02ef948bb build: ipv6disc v0.22.2
