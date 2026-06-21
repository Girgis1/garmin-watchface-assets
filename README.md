# Garmin Watchface Assets

Live image endpoint for the Pulse Orbit Connect IQ watch face test.

- `latest.jpg` is the only background the watch face requests.
- Replace `latest.jpg`, commit, and push to change the watch background wirelessly on the next sync.
- The watch app first resolves the latest `main` commit through the GitHub API, then downloads `latest.jpg` from that commit-pinned raw URL to avoid stale branch-level raw caching.
