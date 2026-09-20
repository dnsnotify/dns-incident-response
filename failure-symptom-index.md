# DNS failure symptom index

The server can be healthy while the public service is broken. Start with the symptom seen by users, then check the public DNS, certificate or registration state that can cause it.

## Website symptoms

| What users see | What to check first | Useful reference |
|---|---|---|
| `This site can't be reached` or `DNS_PROBE_FINISHED_NXDOMAIN` | Confirm the hostname exists at every authoritative nameserver. Check the domain delegation if the whole zone is missing. | [Authoritative DNS lookup](https://dnsnotify.com/dns-lookup/) and [authoritative DNS vs recursive DNS](https://dnsnotify.com/guides/authoritative-dns-vs-recursive-dns/) |
| The website opens for some people but not others after a change | Compare the source answer at the authoritative nameservers with cached answers from recursive resolvers. | [DNS propagation vs DNS monitoring](https://dnsnotify.com/guides/dns-propagation-vs-dns-monitoring/) |
| The website points to the old server | Check A, AAAA and CNAME records at the authoritative nameservers. | [A record lookup](https://dnsnotify.com/a-record-lookup/), [AAAA record lookup](https://dnsnotify.com/aaaa-record-lookup/) and [CNAME lookup](https://dnsnotify.com/cname-lookup/) |
| The website disappears after a nameserver move | Check the parent delegation, the NS set published by the zone, and whether the new nameservers carry the complete zone. | [Nameserver change vs DNS record change](https://dnsnotify.com/guides/nameserver-change-vs-dns-record-change/) and [NS lookup](https://dnsnotify.com/ns-lookup/) |
| A parked page replaces the website | Check domain registration status and expiry, then confirm the nameservers and address records have not changed. | [Domain expiry checker](https://dnsnotify.com/domain-expiry-checker/) and [how to monitor domain expiry](https://dnsnotify.com/guides/how-to-monitor-domain-expiry/) |

## Certificate symptoms

| What users see | What to check first | Useful reference |
|---|---|---|
| `Your connection is not private` or `NET::ERR_CERT_DATE_INVALID` | Read the certificate currently served by the affected hostname, including its expiry date and name coverage. | [SSL certificate checker](https://dnsnotify.com/ssl-certificate-checker/) |
| Renewal completed but browsers still report the old certificate | Test the public endpoint rather than the certificate file on the server. Check every proxy, load balancer and edge endpoint that can terminate TLS. | [Renewed the certificate, but the old one is still served](https://dnsnotify.com/guides/renewed-certificate-old-one-still-served/) |
| Certificate renewals are becoming too frequent to track manually | Automate renewal and verify the certificate actually served from outside the network. | [SSL certificate validity is getting shorter](https://dnsnotify.com/guides/ssl-certificate-validity-is-getting-shorter/) and [how to monitor SSL certificate expiry](https://dnsnotify.com/guides/how-to-monitor-ssl-certificate-expiry/) |
| A certificate authority refuses to issue a certificate | Check the domain's CAA policy and DNSSEC state before retrying. | [CAA record lookup](https://dnsnotify.com/caa-record-lookup/) |

## Email symptoms

| What users see | What to check first | Useful reference |
|---|---|---|
| Senders receive `user unknown`, `recipient not found` or another bounce after a DNS move | Check the domain's current MX records at every authoritative nameserver. Confirm each target is the intended mail provider. | [MX lookup](https://dnsnotify.com/mx-lookup/) |
| The website works but incoming mail has stopped | Check MX independently from the web server, then inspect the A or AAAA records of every MX target. | [Email DNS monitoring](https://dnsnotify.com/email-dns-monitoring/) |
| Messages are rejected after an email-provider change | Check SPF, DKIM and DMARC records exactly as published. Look for stale provider includes, missing selectors and an unexpected policy. | [TXT record lookup](https://dnsnotify.com/txt-record-lookup/) |
| Autodiscover, SIP, XMPP or another service cannot find its endpoint | Check the SRV record's target, port, priority and weight. | [SRV record lookup](https://dnsnotify.com/srv-record-lookup/) |

## Change and monitoring questions

| Question | Useful reference |
|---|---|
| Which records are worth watching? | [Which DNS records should you monitor?](https://dnsnotify.com/guides/which-dns-records-should-you-monitor/) |
| How can an unexpected edit be caught without DNS-provider access? | [Monitoring DNS records for unauthorized changes](https://dnsnotify.com/guides/monitor-dns-records-for-unauthorized-changes/) |
| How do you retain a useful before-and-after history? | [How to monitor DNS changes](https://dnsnotify.com/guides/how-to-monitor-dns-changes/) |
| Does an uptime check cover DNS changes? | [DNS monitoring vs uptime monitoring](https://dnsnotify.com/guides/dns-monitoring-vs-uptime-monitoring/) |
| What should a quiet outside-in monitor check? | [DNS Notify methodology](https://dnsnotify.com/methodology/) |
| Is WHOIS still the right source for registration data? | [RDAP vs WHOIS](https://dnsnotify.com/guides/rdap-vs-whois/) |

## Quick outside-in checks

- [Scan a domain for records across common names](https://dnsnotify.com/dns-scanner/)
- [Check a single record at the authoritative nameservers](https://dnsnotify.com/dns-lookup/)
- [Check the certificate served on port 443](https://dnsnotify.com/ssl-certificate-checker/)
- [Check public domain registration and expiry data](https://dnsnotify.com/domain-expiry-checker/)

These checks describe public state. They do not change DNS, certificates or registrations. For ongoing checks, [DNS Notify](https://dnsnotify.com/) monitors selected public DNS records, nameservers, served certificates and domain registration data, then emails when the monitored state changes.
