## Fixed

- **Session helper: the automatic login did not work on a first start.** In a browser that had never answered it, the portal's cookie dialog covered the login button, so the login was never sent and the helper reported that the portal did not answer. The helper now answers the dialog with "Permitir todas las cookies" before logging in (#17).

If you set up automatic login with 2026.11.4 and got the notification asking you to log in by hand, update the helper: it logs in on its next start.

## Documentation

- Buttons that open the right page of your Home Assistant: add the integration, add the app repository, open the app, the Energy configuration.
- How to read the helper's log to check that the automatic login works.