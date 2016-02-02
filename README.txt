# Gandi-DNSSEC-Tools

== publish-ds-to-gandi ==

Script that is designed to run *on* your master NS (see below for caveat), takes domain name as the first parameter, optional NS IP as a second parameter. Checks the nameserver (defaults to 127.0.0.1) for DNSKEY with 257 flag, checks your Gandi account to see if the domain is in your account, if so checks if the key exists, and if not, uploads it. Won't publish DS unless all nameservers in the zone have the DNSKEY.

Expects config file in one of :

* /etc/gandi.conf
* /usr/local/etc/gandi.conf
* ~/.gandirc

Later files overwrite earlier files.

Expects to find:

apikey some_api_key
endpoint https://rpc.gandi.net/xmlrpc/



You can supply a nameserver as a second argument, however, this should be used with caution. If it pulls a DNSKEY from some other nameserver, before the domain is secure, then you've no way to know it wasn't tampered with. I included this so you can use services such as Cloudflare. The script will output the details of the DS it's publishing, and you really should compare these against those in (in this example) the Cloudflare UI to make sure it's not tampered. You can then independantly verify the chain of trust.

