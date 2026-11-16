## New entities

The Canal publishes consumption with half a day to a day of delay, so the sensor with the liters of the last hour never said much. Each contract now has entities that describe the last day published in full (#20, #21):

| Entity | Shows |
|---|---|
| **Consumo del último día** | Liters of the last full day, with its date as an attribute |
| **Caudal mínimo del último día** | The quietest hour of that day, in L/h. Close to 0 in a house without leaks |
| **Posible fuga** | On when the meter has not rested for a single hour in the last 48 published hours |
| **Datos hasta** | Up to when the Canal has published readings |

- **Posible fuga** can be tuned for each contract, in the configuration section of its device: the flow that counts as rest (1 L/h by default) and the hours without rest that raise it (48 by default). With data a day late it finds the leaks that last, such as a dripping cistern, not a burst pipe.
- The hourly sensor is now called **Consumo de la última hora** and is off by default in new installs. If you already had it, it stays on with the same entity id.
- The meter reading and the hourly statistic for the Energy panel are unchanged.

## Fixed

- After the portal refused a login, the notice of an earlier failed try stayed next to the request for the credentials (#19).
- The notices link to the session helper's browser with a readable link instead of a bare address (#19).
- Session helper: no double period in its log when the portal's message ends in one.

No changes to the setup: update the integration, restart Home Assistant, and update the session helper when convenient.