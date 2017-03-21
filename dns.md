#### Let's Google!

We need an ip address for `www.gooogle.com`

* Operating systems check the host file 
* Check local DNS cache
* Ask home network router cache and hosts file
* Check DNS cache at ISP, not in cache? iterate!
* Ask root servers where `.com` lives
* Ask `.com` authoritave server where `google.com` lives
* Ask `google.com` authotiative server for `www.google.com` IP Address

*You can use `nslookup` to check primary answer or `dig` to see the full path*

#### Two types of servers

* Authoritative *Owns the domain*
* Cache (recursor) *Resolves the domain for you*

### DNS

Designed in 1983 by Paul Mockapetris (UCal Irvine)
Converts hostnames ot IP addresses
Stores mail delivery information for a domain (MX records)
Stores other information for a domain (TXT records)

All TLDs can enforce there own rules.
*Ex. Only canadians can register a `.ca` domain name*

### Root Servers

Maintained by ICANN, [root-servers.org](http://root-servres.org)
You can become your own top level domain. Check IANA, costs >$100,000 per year.

ORSN  Open Root Server Network
* Mirrors iCANN root servers
* Reduce over-dependance on the USA
* "independant mode" in case a political situation requires it

#### DNS Zones
* This is nameservers you mark with your domain host so they point to your server properly.

Typical records
* NS - which are my nameservers
* A - IPv4 address
* AAAA - IPv6 address pointer
* CNAME - Reference to another record, not a redirect
* MX - Mail exchangers for the domain, with priorities
* TXT - Textual values, often used to validate domain ownership
* SRV - Describes a service type and port

#### PTR
Reverse DNS used for diagnostic tools like ping and traceroute.
Email anti-spam uses this as well.

#### Zone transfer
* Usually more than one nameserver for a zone
* 1 primary, other secondaries
* No need to maintain zones on every slave!

#### Security
DNS Cache poising

* Can spoof other services without a browser noticing by IPs to other ones

#### DNSSEC (domain name secutity extensions)

* Set of extensions to DNS
* Origin verification
* Prevents cache poisoning

#### DNS amplification for DDoS

* DNS recusion is awesome! (and often default)
    * Lots of DNS servers out there have recursion enabled for all
    * Lots of open resolvers out there
* Saturate a victim's network connection by using open DNS resolvers
    * UDP connections don't allow verification of requesters IP address

Attacker -> Open DNS resolver -> Victim

* Make sure to disable recursion
    * Or limit it to known trusted networks
    

#### CDN

Serve origin content from edge location close to the user

#### Service Discovery

Host a dns server as part of your application

* UPnP
* SLP
* Zeroconf

#### Fun

Connect to wifi
Captive portal
    * Usually intercepts HTTP(S) only
    * Usually allows DNS lookups
Proxy HTTP to DNS