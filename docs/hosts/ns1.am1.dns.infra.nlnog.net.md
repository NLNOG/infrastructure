# PowerDNS
The PowerDNS installation tracks the 4.0.X branch of the PowerDNS Authoritative server.

For now, the zone can be edited by logging into the machine and running `sudo pdnsutil edit-zone infra.nlnog.net`. Don't forget to bump the SOA serial!

## Manually performed steps
After installing these commands have been run by hand:

 * `sudo pdnsutil create-zone infra.nlnog.net`
 * `sudo pdnsutil secure-zone infra.nlnog.net`
