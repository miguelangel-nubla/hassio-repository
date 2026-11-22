## What's new

* **OpenWrt: an update ends once dnsmasq answers with the new records.** Reloading dnsmasq only signals it, so an update could return a moment before the records were served. The provider now asks the router's own dnsmasq, at `127.0.0.1`, until it answers with them. If dnsmasq answers but never with the new records, the update fails after 10 seconds and says so. Where dnsmasq is on another port, there is more than one dnsmasq, or nothing answers at `127.0.0.1`, nothing is asked and the update ends as before.
* **The report says `1 name`**, not `1 names`, in its summary and in a resolver's zones.
* **The README shows the report with its colors**, as a picture, and so does the resolver's page for its part of the report.
* **The Home Assistant guide says which integrations keep a name.** An integration that keeps the host name you type, such as MQTT, follows the name when the device's address changes. Shelly and ESPHome store the address, and Home Assistant finds those again by discovery.

Nothing in the configuration changes.

## Changelog
* ba2a65f fix: one name is counted as 1 name, on the report
* d8bdc5c docs: which integrations keep a name, and which keep its address
* f1c9084 docs: the README shows the report with its colors, as a picture drawn from its text
* ffb00d8 docs: the resolvers' report as a picture too, and each picture drawn from a text beside it
* beeaa71 fix(docs): the pictures are the same on every machine: their numbers are whole
* bb982f9 fix(openwrt): an update ends once dnsmasq answers with its records, not when its reload is asked for
