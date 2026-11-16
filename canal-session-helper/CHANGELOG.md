## One automatic setup

The integration now asks for your document, password and profile of the virtual office when you add it, and the session helper logs in with them whenever the integration is about to read data. Nothing else has to be configured, and you only step in when the portal asks for a captcha or refuses the login (#18).

- **Sessions on demand.** The helper logs in only when data is due, about twice a day, instead of both sides checking the portal every 10 minutes to keep a session alive.
- **Problems are shown by Home Assistant.** A refused login asks for your credentials again; a captcha, a portal that does not answer or a helper that is not running appear under Repairs and clear by themselves.
- **The helper has no settings about your account.** As a Home Assistant app it needs no configuration; as a container, only `HA_URL`, the token and the VNC password.

## Upgrading (breaking)

Update the integration and the session helper **together**.

- Home Assistant will ask once for your document and password. Your history is kept.
- The helper's options `document`, `password`, `profile`, `entry_id` and `check_interval` (`CANAL_DOCUMENT`, `CANAL_PASSWORD`, `CANAL_PASSWORD_FILE`, `CANAL_PROFILE`, `HA_ENTRY_ID`, `CHECK_INTERVAL`) are gone: remove them from your compose file.
- Setting the integration up by pasting a `JSESSIONID` cookie is no longer offered. The session helper is required.

Setup is described in the [README](https://github.com/miguelangel-nubla/homeassistant_canal_isabel_II#configuración) and the [helper's guide](https://github.com/miguelangel-nubla/homeassistant_canal_isabel_II/blob/main/canal-session-helper/DOCS.md).