# Email-provider DNS change runbook

Use this when changing mail providers, gateways, DMARC services or DKIM selectors. The operational goal is to detect a broken mail path before a client reports that no messages have arrived for hours.

## Capture and validate

- Record MX targets, priorities and their address records.
- Follow every SPF `include` and `redirect` dependency and count DNS-causing lookups.
- Record active DKIM selectors and follow selector CNAMEs.
- Check DMARC policy, reporting addresses and organizational-domain fallback.
- Include MTA-STS, TLS reporting and provider-verification records where used.
- Query every authoritative server directly for each changed name.
- Send test messages in both directions and inspect received authentication results.

Use the free [DNS Notify MX lookup](https://dnsnotify.com/mx-lookup/) and [DNS scanner](https://dnsnotify.com/dns-scanner/) for a quick outside-in snapshot.

## Prevent a client-discovered outage

- Keep old routing or signing configuration for the planned overlap.
- Monitor critical records for unexpected additions, removals and value changes.
- Alert the responsible team before the client notices missing mail.
- Retire obsolete selectors and verification records only after confirming they are unused.
- Document who owns each external dependency and where alerts go.

**DNS Notify** can watch public DNS state without DNS-provider credentials when the team does not want to maintain its own polling and comparison job.
