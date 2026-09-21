# Prevent client-discovered DNS, email and certificate outages

A client's phone call should not be the first alert that their website is down or their email stopped arriving.

**Printable one-page PDF:** [Five Things to Monitor After Every Client Website Goes Live](../assets/client-website-monitoring-checklist.pdf)

## For every client domain

- [ ] Monitor authoritative nameservers and critical DNS records from outside the provider account.
- [ ] Alert on added, removed and changed A, AAAA, CNAME, MX, NS and important TXT records.
- [ ] Check that every authoritative server gives a consistent answer.
- [ ] Monitor the certificate actually served by the public endpoint, not only the file on disk.
- [ ] Track domain registration expiry separately from certificate expiry.
- [ ] Route alerts to a maintained team address with a named escalation owner.
- [ ] Record the expected value and approved change window so routine work does not create noise.
- [ ] Test the alert path and the renewal or rollback procedure.

## When an alert arrives

1. Confirm the result from another network or resolver.
2. Query authoritative servers directly and preserve timestamps.
3. Compare the change with the approved work log.
4. Restore service or escalate before the client is affected long enough to notice.
5. Record the root cause and add a check that catches the same failure earlier.

A small scheduled script can handle these checks if someone owns it. **DNS Notify** provides hosted outside-in DNS change, SSL certificate and domain-expiry monitoring for teams that would rather pay a small predictable amount than maintain another monitoring job—or explain a preventable outage to a client.
