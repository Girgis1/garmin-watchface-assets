# Garmin Watchface Assets

Live image endpoint for the Pulse Orbit Connect IQ vivoactive 6 watch face.

- `latest.jpg` is the only background the watch face requests.
- `latest_meta.json` is the optional contextual-link payload for that same
  commit.
- Replace `latest.jpg`, commit, and push to change the watch background wirelessly on the next sync.
- Publish `latest.jpg` and `latest_meta.json` in the same commit when the top
  half should open weather, news, train, moon, or another related link on the
  phone.
- The watch downloads `latest.jpg` and `latest_meta.json` from `main` with a
  per-sync query value (`?v=<epoch>`) to avoid stale branch-level raw caching.
- Do not add the unauthenticated GitHub commits API to the watch path. Garmin
  received HTTP 403 from that endpoint. The publisher, not the watch, verifies
  the commit-pinned remote files before declaring a publish successful.

Recommended publisher:

```powershell
C:\GitProjects\Garmin\watchfaces\vivoactive6-starter\scripts\publish-latest-image.ps1 -SourceImage C:\path\to\source.png
```

Jetson/Hermes should use the canonical publisher directly when metadata is
available:

```bash
python3 /home/nicebot/.hermes/Garmin/scripts/garmin_publish_image.py \
  --image /path/to/watchface.png \
  --meta-file /path/to/latest_meta.json
```

Recommended verifier:

```powershell
C:\GitProjects\Garmin\watchfaces\vivoactive6-starter\scripts\verify-live-image.ps1
```
