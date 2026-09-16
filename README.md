# keepalive-hub

One GitHub Action that keeps **all** my Supabase free-tier projects from pausing.

Every 2 days it pings each project's REST API (a real query with the public anon
key). A second job uses `keepalive-workflow` to auto-commit a heartbeat before
GitHub's 60-day scheduled-workflow auto-disable — so it runs **forever** with no
manual action.

Projects covered: booking-barbershop, booking-other, metaxumas, spacers, noobs,
eprepe.

To add a project: append an entry to the `matrix.include` list in
`.github/workflows/keepalive.yml` (url + a table name + the public anon key).

## Also here: noobs.gr content sync

`.github/workflows/noobs-basketaki-sync.yml` pings
`https://noobs.gr/api/sync-basketaki` every 15 minutes. That endpoint rebuilds
the site's standings, schedule and results from the club's official
basketaki.com pages and looks up the YouTube stream of each played game. The
site also re-syncs on every visit; this heartbeat is what makes a match-day
update land even when nobody opens the site. The endpoint is public, throttles
itself to one scrape per 10 minutes and writes nothing when nothing changed, so
no secret is needed here.
