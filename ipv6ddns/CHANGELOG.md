## Upgrade notes

- **A source that works replaces its addresses.** Before, an address a source no longer gave stayed for its lifetime: when the network's public address changed, the old one stayed in the A record beside the new for three intervals, 15 minutes by default. Now a run that works gives the source's addresses, and the old one goes at once. A run that fails, for all or a part, still keeps them for their lifetime, through an outage of the service asked.
- **ipv6ddns starts without discovery** when there is nothing to discover, no plugins and no family listening: a configuration of sources only, as the public address, no longer stops the start.

## New: Home Assistant integration

ipv6ddns is a device of Home Assistant's ESPHome integration, which every Home Assistant has: no custom integration to install. See [the documentation](https://github.com/miguelangel-nubla/ipv6ddns/blob/main/docs/home-assistant-integration.md).

```yaml
homeassistant: {}
```

- Home Assistant finds it by mDNS, and adds it without asking anything: as to ESPHome's devices, it makes the encryption key and gives it, and ipv6ddns keeps it in `homeassistant.state`. Or set your own, `key:`, which Home Assistant asks for and can't change.
- **In Home Assistant**: each name's addresses, last update and update problem, the hosts discovered, and an *Update now* button.
- **From Home Assistant**: a `homeassistant` source reads the addresses in an entity's state, or attribute, as a router's WAN address sensor. A change runs it at once.
- Until it has its key, the device takes connections without one, for Home Assistant to give it: they see its entities, but their states and button presses are dropped, so nobody can give a source an address.
- In the add-on, it is on in the starting configuration of new installs. On an existing one, add `homeassistant: {}` to its `config.yaml`.

Tested with aioesphomeapi, the library Home Assistant's integration uses, in CI, and against Home Assistant OS 18.4.

## Changelog
* 82bded513250de5840323561ebc21c15b7e0c7fe feat(homeassistant): Home Assistant gives the key, as to ESPHome's devices
* 043b18eee8d4801fa03b8fa0d047eaeab9dd6e94 feat(homeassistant): announce, to turn the mDNS announcement off
* 9bc7d2916f05b0919f7bc8c0e2e16ac2d10ee060 feat: a device of Home Assistant's ESPHome integration, and homeassistant sources
* dba7c12cc58d8b8e1ac4c5d2147fe401f9d6c5bc fix(esphome): answer the device capabilities Home Assistant waits for
* b108b0b8a6f2205b8949f41fb99ba3b7f8e26299 fix(source): a run that works replaces the addresses
* 36b95acdbaa430c39434c8084e81a801b196dce7 fix: start without discovery when there is nothing to discover


