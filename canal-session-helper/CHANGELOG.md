## Integration

- A setup that cannot read the portal now loads anyway, keeps the session alive and tries again in 10 minutes, instead of retrying the whole setup every minute or so.
- The periodic download no longer stops when there are no sensors, and the sensors appear when data first arrives.
- Only a redirect to the login page counts as the end of a session. Other answers from the portal (maintenance, errors) no longer mark a live session as ended.
- Adding or renewing a session now tells "the portal did not accept it" apart from "the portal could not be reached". Renewing no longer downloads the whole year again.
- Two downloads in a row no longer restart the running total.
- Errors while asking for hourly data or downloading the CSV are reported instead of importing nothing.
- Canal de Isabel II icon and logo.

## Session helper (container and add-on)

- The session survives a restart of the container or the browser.
- Waiting for a login no longer reloads the page every few seconds, and the "login needed" notification is retried if Home Assistant was not reachable.
- As an add-on, only Home Assistant itself can reach the logged-in browser.
- A restarted container starts cleanly.

## Known limitations

- With several contracts on one account, only the one the portal shows selected is read.