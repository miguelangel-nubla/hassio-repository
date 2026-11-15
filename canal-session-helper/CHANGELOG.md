## Breaking

Hourly consumption is now stored as the statistic **Canal de Isabel II `<contract>`** (`canal_de_isabel_ii:consumption_<contract>`), and the old "Total" entity is removed. Select the water source in the Energy panel again once.

## Fixed

- Connections failing with `CERTIFICATE_VERIFY_FAILED` since the portal renewed its certificate on 2026-11-10: its server no longer sends the intermediate certificate, which is now bundled.
- Negative bars in the Energy panel: each import continues the stored series.

## New

- The first download imports the last year of hourly consumption; later ones re-read the last 30 days, so late readings and gaps fill in by themselves.
- Meter reading sensor (m³), the figure used on the bill.
- Each session's lifetime is recorded and shown in the entry diagnostics. Keep-alive every 10 minutes.
- Service `canal_de_isabel_ii.set_session`, to hand the integration a new session from outside.
- **Session helper**: a browser in a container where you log in to the virtual office yourself; it then hands the session to the integration and watches it. Available as a Docker image (`ghcr.io/miguelangel-nubla/canal-session-helper`) and as a Home Assistant add-on from https://github.com/miguelangel-nubla/hassio-repository. See `canal-session-helper/`.
- Translations (English, Spanish), tolerant CSV parsing, tests and CI.