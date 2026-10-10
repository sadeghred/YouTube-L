# YouTube Session & Recovery

YouTube can present login or automated-access challenges depending on network, account, and request conditions.

The project therefore uses:

- Real Google Chrome
- Persistent Chrome profile
- Authenticated Google/YouTube session
- Browser session/cookie reuse by the downloader core
- Recovery logic when session health fails

## Session Lifecycle

1. A real YouTube-related request arrives.
2. Session health is evaluated.
3. Healthy session: processing continues.
4. Unhealthy session: automatic recovery is attempted.
5. If automatic recovery is insufficient, the browser state is diagnosed.
6. The administrator receives a private alert.
7. Manual login/recovery can be performed through SSH tunnel + noVNC.
8. Session health is checked again.

Periodic session polling is intentionally disabled; validation is event-driven.
