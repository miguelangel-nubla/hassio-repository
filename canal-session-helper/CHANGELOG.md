## Automatic login

The session helper now logs in to the virtual office by itself. Give it your document and password and it logs in at start and every time the portal ends the session, so the integration keeps running without anyone having to step in (#15).

- **Add-on:** fill in `document` and `password` (and `profile` if it is not `particular`) in the add-on's configuration.
- **Container:** set `CANAL_DOCUMENT` and `CANAL_PASSWORD` (or `CANAL_PASSWORD_FILE`), and `CANAL_PROFILE` if needed.
- Without credentials the helper works as before: you log in by hand in its browser.

The login form runs an invisible captcha, which the helper neither answers nor avoids. When a login does not go through, a Home Assistant notification says why and you can log in by hand in the helper's browser:

- A login the portal refuses is retried after 1 hour and after 6 more, then no more until the credentials change or you log in by hand, so a wrong password cannot lock the account.
- A captcha challenge is left on screen for you and the login is retried an hour later.
- If the portal does not answer, the login is retried after 5, 15 and 30 minutes, then hourly.

Details in the [helper's guide](https://github.com/miguelangel-nubla/homeassistant_canal_isabel_II/blob/main/canal-session-helper/DOCS.md).