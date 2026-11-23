# Client domain handover template

Use this at website handover or when adding a client to a care plan. Keep one copy per business domain. Record account owners and response contacts; keep passwords in the team's password manager.

## Ownership and response

| Item | Provider | Account owner | Response contact |
| --- | --- | --- | --- |
| Domain registration | | | |
| Authoritative DNS | | | |
| Website hosting or CDN | | | |
| Business email | | | |
| Contact-form sending service | | | |

**Client domain:**

**Website hostnames, including redirects:**

**Launch or last agreed change:**

**Person receiving monitoring alerts:**

## Accepted public values

| Check | Working value or saved snapshot | Checked on |
| --- | --- | --- |
| Delegated nameservers | | |
| Apex website A / AAAA / CNAME | | |
| `www` A / AAAA / CNAME | | |
| MX targets and priorities | | |
| SPF TXT policy | | |
| Active DKIM selector names and TXT / CNAME records | | |
| DMARC TXT policy | | |
| Public certificate expiry for each website hostname | | |
| Published domain-registration expiry | | |

Keep a zone export with the project notes. Confirm the registrar and mail-service owners before a nameserver move.

## Handover checks

- [ ] Public website records match the agreed hosting configuration.
- [ ] Every intended authoritative nameserver returns the agreed records.
- [ ] An external test email arrives and the reply authenticates as intended.
- [ ] A contact-form enquiry reaches the intended inbox.
- [ ] The website serves the intended certificate for each public hostname.
- [ ] Domain expiry and the renewal owner are recorded.
- [ ] The client knows which contact receives and investigates monitoring alerts.

Use the [DNS scanner](https://dnsnotify.com/dns-scanner/), [email DNS checker](https://emaildns.gitlab.io/), [certificate checker](https://dnsnotify.com/ssl-certificate-checker/) and [domain expiry checker with calendar reminders](https://domain-expiry.pages.dev/) for public checks.

## After a monitored change

1. Compare the alert with planned work.
2. Check the public answer and identify the provider that controls it.
3. Contact the responsible person above.
4. Verify the intended public result after the repair or planned change.
5. Update the accepted baseline and handover record.

The [website care-plan checklist](https://dev.to/dnsnotify/a-domain-monitoring-checklist-for-website-care-plans-3ph1) explains the ongoing process. Before changing nameservers, follow the [email DNS migration checks](https://dev.to/dnsnotify/preserve-email-dns-when-moving-a-client-website-307i).

For ongoing independent checks, [DNS Notify](https://dnsnotify.com/domain-monitoring/) monitors selected public DNS records, nameservers, served certificates and registration data without provider credentials. It is £5/month for five domains, with a [seven-day no-card trial](https://dnsnotify.com/signin).

Prepared by Mira John.
