# Gandi-DNSSEC-Tools

== publish-ds-to-gandi ==

Script that is designed to run *on* your master NS, takes domain name as the only parameter. Checks localhost for DNSKEY with 257 flag, checks your Gandi account to see if the domain is in your account, if so checks if the key exists, and if not, uploads it. Won't publish DS unless all nameservers in the zone have the DNSKEY.