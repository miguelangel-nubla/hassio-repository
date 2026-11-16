## Fixed

- **Session helper: a browser with saved passwords no longer gets in the way.** If you logged in by hand in the helper's browser and let it save your credentials, the browser then filled the login form in by itself. The helper took that for a person typing and waited, or its own text ended up next to the browser's (a document number written twice). It now writes over whatever is in the form and checks the result, and only steps aside while someone is really typing (#35, reported in #16).

## Display

- The two leak settings have shorter names, which the device page no longer cuts: **Fuga: caudal de reposo** and **Fuga: horas sin reposo**.
- The meter reading is shown with three decimals, as on the bill, and the minimum flow with two (#34).

Update the session helper and the integration, and restart Home Assistant.
