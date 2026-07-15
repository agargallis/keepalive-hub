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
