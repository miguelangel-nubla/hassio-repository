## Fixed: every hour was stored one hour late

The Canal labels each hour with the moment it **ends**: today's "00" row is yesterday's last hour. The integration took the label for the start, so consumption appeared one hour later than it happened, and the last hour of each day was counted with the next day (#33).

- Checked against the meter's own reading: between two readings 24 hours apart the meter advanced 382 L, which is what the hourly rows add up to only when read this way.
- **On updating, the stored history moves one hour back by itself, once.** Liters and totals do not change; the split by days does.
- Both clock-change days are handled.

## New

- **Every contract of the account is read**, each with its own device, up to 20 (#26). Not yet tried on a real account with several contracts: please open an issue if something is off.
- **The session helper keeps its browser current.** Once a month, if Debian has a newer Chromium, a maintenance release is published with it (#25).
- **Health check.** The helper's container reports `healthy` while it works, and ends itself to be restarted if it ever stalls (#25).
- **Verifiable image.** Each image carries its bill of materials and a signed statement of where it was built: `gh attestation verify oci://ghcr.io/miguelangel-nubla/canal-session-helper:2026.11.10 --repo miguelangel-nubla/homeassistant_canal_isabel_II` (#25).
- **AppArmor profile for the app**, which confines the browser inside its container (#28).
- **Documentation in English**: [README](https://github.com/miguelangel-nubla/homeassistant_canal_isabel_II/blob/main/README.en.md) and [helper guide](https://github.com/miguelangel-nubla/homeassistant_canal_isabel_II/blob/main/canal-session-helper/DOCS.en.md).

## Behind the scenes

- A release is now published only once its helper image exists (#24).
- Build dependencies are pinned and kept up to date by Dependabot (#25, #32).
- Icons and internal state follow Home Assistant's current conventions (#27).

Update the integration and the session helper, and restart Home Assistant.
