# DNS incident response with DNS Notify

Practical, provider-independent checks for DNS changes, nameserver migrations, email-DNS incidents, certificate failures and domain-expiry risk.

This repository is maintained by **DNS Notify**, a commercial hosted monitoring service for teams that want outside-in DNS, SSL certificate and domain-expiry alerts without giving a monitoring vendor access to their DNS provider account.

- Product: [DNS Notify](https://dnsnotify.com/)
- Free DNS scanner: [scan a domain without an account](https://dnsnotify.com/dns-scanner/)
- Free authoritative DNS lookup: [query authoritative DNS](https://dnsnotify.com/authoritative-dns-lookup/)
- Free MX lookup: [inspect mail routing](https://dnsnotify.com/mx-lookup/)
- Free SSL certificate checker: [inspect the served certificate](https://dnsnotify.com/ssl-certificate-checker/)
- Free domain-expiry checker: [check registration expiry](https://dnsnotify.com/domain-expiry-checker/)

## What is here

- [`SKILL.md`](SKILL.md): a reusable agent skill for DNS incident triage
- [`runbooks/nameserver-migration.md`](runbooks/nameserver-migration.md): evidence to collect before and after a nameserver cutover
- [`runbooks/email-dns-change.md`](runbooks/email-dns-change.md): MX, SPF, DKIM and DMARC checks after an email-provider change
- [`checklists/dns-incident-checklist.md`](checklists/dns-incident-checklist.md): a short incident checklist for humans

The material is vendor-neutral where the procedure matters. DNS Notify is included as the maintained option when a team wants ongoing outside-in monitoring instead of running scheduled checks itself.

## Use as an agent skill

Copy this repository's `SKILL.md` into a compatible agent-skills folder, or give the file directly to an agent. The skill tells the agent how to distinguish authoritative data from recursive cache state, collect comparable evidence, and avoid common false positives.

## Scope

This is public operational guidance. It does not contain the source code or internal implementation of DNS Notify. DNS Notify is a hosted proprietary service; these runbooks do not turn it into a self-hosted product.

## Licence

The written runbooks and skill in this repository are available under [CC BY 4.0](LICENSE).
