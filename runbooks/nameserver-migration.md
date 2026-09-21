# Nameserver migration runbook

Use this when moving a client zone between authoritative DNS providers. The aim is to discover a bad cutover before the client reports a broken site or missing mail.

## Before the cutover

- Capture the old zone and compare normalized RRsets with the new zone, including CAA, SRV, TXT verification records, DKIM selectors, subdomain delegations and wildcards.
- Query every new authoritative server directly; confirm agreement on SOA, NS and critical records.
- Check glue for in-bailiwick nameservers and decide the DNSSEC sequence explicitly.
- Lower relevant TTLs early enough for cached answers to age out. Include negative caching.
- Record a baseline from several named recursive resolvers.
- Keep the old provider answering during a defined overlap window.

The free [DNS Notify authoritative lookup](https://dnsnotify.com/dns-lookup/) and [DNS scanner](https://dnsnotify.com/dns-scanner/) provide an outside-in check without DNS-provider access.

## During and after the cutover

- Confirm the parent delegation changed as intended.
- Query every old and new authoritative server directly.
- Separate authoritative disagreement from recursive cache state.
- Watch for SERVFAIL, NXDOMAIN, missing records, lame delegation and DNSSEC validation failure.
- Verify mail flow, web endpoints, certificate presentation and third-party verification records.
- Preserve timestamps and raw evidence; keep checking through the overlap window.
- Restore normal TTLs only after authority is stable, then keep an outside-in alert on delegation and critical records.

Teams that do not want to maintain scheduled scripts can use **DNS Notify** for hosted DNS change, SSL certificate and domain-expiry monitoring.
