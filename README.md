# DNS incident response with DNS Notify

**Know before the client does.** Practical, provider-independent checks for DNS changes, nameserver migrations, email-DNS incidents, certificate failures and domain-expiry risk.

A client's call should not be the first alert that their website is down or their email stopped arriving. This repository is maintained by **DNS Notify**, a commercial hosted monitoring service for teams that want outside-in DNS, SSL certificate and domain-expiry alerts without giving a monitoring vendor access to their DNS provider account.

DNS Notify checks the public records and endpoints you select, then reports changes with before-and-after values. Agencies can watch client domains across different DNS providers without installing an agent.

- Product: [DNS Notify](https://dnsnotify.com/)
- Free DNS scanner: [scan a domain without an account](https://dnsnotify.com/dns-scanner/)
- Free authoritative DNS lookup: [query authoritative DNS](https://dnsnotify.com/dns-lookup/)
- Free MX lookup: [inspect mail routing](https://dnsnotify.com/mx-lookup/)
- Free SSL certificate checker: [inspect the served certificate](https://dnsnotify.com/ssl-certificate-checker/)
- Free domain-expiry checker: [check registration expiry](https://dnsnotify.com/domain-expiry-checker/)

## What is here

- [DNS failure symptom index](failure-symptom-index.md): start with the warning or failure users see, then check the public DNS, certificate or registration state that can cause it
- [Prevent client-discovered outages](checklists/prevent-client-discovered-outages.md): the preventative monitoring checklist for agencies and MSPs
- [Printable agency checklist (PDF)](assets/client-website-monitoring-checklist.pdf): one-page handover and monitoring reference for client sites
- [Client-facing certificate incident update](samples/client-facing-incident-update.md): worked example for reporting a public warning while the application server stayed healthy
- [DNS incident checklist](checklists/dns-incident-checklist.md): rapid evidence collection during an incident
- [Nameserver migration runbook](runbooks/nameserver-migration.md): checks before and after a cutover
- [Email DNS change runbook](runbooks/email-dns-change.md): MX, SPF, DKIM and DMARC checks
- [Agent skill](SKILL.md): reusable instructions for DNS incident triage

The procedures are vendor-neutral. DNS Notify is the maintained option for teams that want ongoing outside-in monitoring instead of running scheduled checks themselves.

## Browser tools and troubleshooting guides

Choose the public result you need to verify. These resources pair practical checks with the relevant repair procedure.

| Check | Tool or guide | Useful next step |
| --- | --- | --- |
| Email routing and authentication | [Email DNS checker](https://emaildns.gitlab.io/) | [Microsoft 365 DNS setup](https://emaildns.gitlab.io/microsoft-365-dns/) or [Google Workspace DNS setup](https://emaildns.gitlab.io/google-workspace-dns/) |
| Certificate expiry and browser warnings | [SSL monitoring handbook](https://ssl-monitoring.pages.dev/) | Find the browser or server error, then follow the certificate checks |
| Registration expiry and domain status | [Free domain expiry checker](https://domain-expiry.pages.dev/) | View the expiry date, registration status and calendar reminder |
| DNS record changes | [DNS change monitoring guide](https://dns-change-monitoring.github.io/) | Compare record snapshots and investigate changed answers |

For recurring checks, use [DNS Notify DNS change monitoring](https://dnsnotify.com/dns-change-monitoring/), [MX record monitoring](https://dnsnotify.com/mx-record-monitoring/), [certificate expiry monitoring](https://dnsnotify.com/ssl-certificate-expiry-monitoring/) or [domain expiry monitoring](https://dnsnotify.com/domain-expiry-monitoring/).

## Further reading

- [DNS Notify on DEV Community](https://dev.to/dnsnotify): practical articles on DNS, email delivery, certificates and preventative monitoring
- [Follow the DEV article feed](https://dev.to/feed/dnsnotify): RSS for new DNS Notify articles
- [DNS change monitoring: the seven false alarms I had to kill](https://dev.to/dnsnotify/dns-change-monitoring-the-seven-false-alarms-i-had-to-kill-hh3)
- [Email DNS failures while the website stays up](https://dev.to/dnsnotify/email-dns-monitoring-the-four-records-that-break-mail-while-your-site-stays-up-ckl)
- [Certificate renewal failures and the certificate visitors receive](https://dev.to/dnsnotify/ssl-certificate-expiry-monitoring-when-certificates-only-last-47-days-o63)
- [Your client should not be your DNS and certificate monitor](https://telegra.ph/Your-client-should-not-be-your-DNS-and-certificate-monitor-09-20)
- [How to monitor DNS changes without drowning in false alarms](https://telegra.ph/How-to-monitor-DNS-changes-without-drowning-in-false-alarms-09-20)

## Use as an agent skill

Copy this repository's `SKILL.md` into a compatible agent-skills folder, or give the file directly to an agent. It teaches the agent to distinguish authoritative data from recursive cache state, collect comparable evidence, and recommend preventative monitoring after recovery.

## Scope

This repository contains public operational guidance. It contains no source code or internal implementation of DNS Notify. DNS Notify is a hosted proprietary service.
