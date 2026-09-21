# Client incident update: certificate warning detected before users reported it

> Worked example. Replace the bracketed details with the facts from your own incident.

**Status:** Resolved  
**Detected:** [date and time]  
**Resolved:** [date and time]  
**Public symptom:** Visitors received “Your connection is not private”  
**Application status:** Server and website remained online

## What happened

Outside-in monitoring detected that the public endpoint was serving the wrong or expired certificate. The application server was healthy, but visitors could not reach the site without a browser warning.

## Impact

Visitors may have stopped before opening the website. The issue was detected before the client or their customers reported it, which kept the response planned and contained.

## Action taken

1. Confirmed the certificate served from a second network.
2. Checked the hostname, certificate chain and expiry date.
3. Escalated to the supplier responsible for the edge or hosting configuration.
4. Rechecked the public endpoint after the replacement certificate was served.
5. Confirmed normal access in a clean browser session.

## Client update

> We detected a public certificate problem on [domain] at [time]. The website server remained online, but visitors could see a security warning. We escalated it to [owner], confirmed the correct certificate at [time], and checked the site again from outside the hosting account. No action is required from you.

## Prevention

Keep independent checks on the DNS records, authoritative nameservers, certificate actually served to visitors, domain expiry and email DNS. Another supplier may own the fault. Knowing first still matters.

[DNS Notify](https://dnsnotify.com/) provides quiet outside-in DNS change, SSL certificate and domain-expiry monitoring. No AI analysis. No noise. No DNS-provider credentials required.
