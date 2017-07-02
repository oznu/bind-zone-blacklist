[![Travis branch](https://img.shields.io/travis/oznu/dns-zone-blacklist/master.svg)](https://travis-ci.org/oznu/dns-zone-blacklist)

# DNS Zone Blacklist Generator

This project generates a zone file for Bind, Dnsmasq and Unbound DNS servers. It can be used to create DNS based AD Blockers such as [oznu/dns-ad-blocker](https://hub.docker.com/r/oznu/dns-ad-blocker/).

The blacklist is generated using data from the [StevenBlack/hosts](https://github.com/StevenBlack/hosts) project which is extending and consolidating hosts files from a variety of sources like adaway.org, mvps.org, malwaredomains.com, someonewhocares.org, yoyo.org, and potentially others.

Since DNS based AD Blockers can support wildcard entries, this tool filters out any subdomains of known adware or malware domains, reducing the number of BIND entries required from over 36,000 to just under 25,000.

| DNS Server | Response Type | Download  | SHA256 Checksum |
| ---------- |:-------------:|:---------:|:---------------:|
| Bind | 0.0.0.0 | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/bind/zones.blacklist) | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/bind/zones.blacklist.checksum) |
| Dnsmasq | 0.0.0.0 | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/dnsmasq/dnsmasq.blacklist) | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/dnsmasq/dnsmasq.blacklist.checksum) |
| Dnsmasq | NXDOMAIN | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/dnsmasq/dnsmasq-server.blacklist) | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/dnsmasq/dnsmasq-server.blacklist.checksum) |
| Unbound | 0.0.0.0 | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/unbound/unbound.blacklist) | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/unbound/unbound.blacklist.checksum) |
| Unbound | NXDOMAIN | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/unbound/unbound-nxdomain.blacklist) | [link](https://raw.githubusercontent.com/oznu/dns-zone-blacklist/master/unbound/unbound-nxdomain.blacklist.checksum) |

## Blacklist Updates

The blacklists are updated every 24 hours with the latest data from [StevenBlack/hosts](https://github.com/StevenBlack/hosts).

## Building the Blacklist

The blacklist can be generated using [Node.js 6.9.1](https://nodejs.org) or later.

Install:

```
git clone https://github.com/oznu/dns-zone-blacklist.git
cd dns-zone-blacklist

npm install
```

Then build:

```
node build/index.js
```

The updated blacklist files will be saved to the ./bind and ./dnsmasq directories in the root of the project.

### Custom Entries

Custom entries can be added to the custom.blacklist.json file in the root of this project before building.

### Whitelist

Any domains you wish to exclude from the blacklist can be added to the custom.whitelist.json file in the root of this project before building.
