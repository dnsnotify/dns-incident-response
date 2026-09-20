# DNS incident checklist

- [ ] Write down the expected answer and the time the change was made.
- [ ] Check the parent delegation and glue.
- [ ] Query every authoritative server directly.
- [ ] Compare RRsets, RCODE, AA, TTL and DNSSEC state.
- [ ] Query a few named recursive resolvers and note remaining TTL.
- [ ] Check negative caching after NXDOMAIN or NODATA.
- [ ] Test UDP and TCP when responses are large or intermittent.
- [ ] Follow CNAMEs and external dependencies.
- [ ] Inspect the certificate served by the public endpoint.
- [ ] For mail incidents, check MX, SPF, DKIM and DMARC separately.
- [ ] Preserve timestamps and evidence before making another change.
- [ ] Add an outside-in check after recovery so recurrence is caught before the client reports it.

The [DNS Notify free tools](https://dnsnotify.com/dns-scanner/) cover browser-based DNS, MX, SSL and domain-expiry checks. **DNS Notify** provides ongoing hosted alerts for teams that do not want to maintain the checks themselves.
