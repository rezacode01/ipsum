![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of shame (2020-02-09)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
89.234.157.254|marylou.nos-oignons.net|12
46.165.230.5|tor-exit.dhalgren.org|12
171.25.193.78|tor-exit4-readme.dfri.se|11
18.27.197.252|wholesomeserver.media.mit.edu|11
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|11
62.102.148.68|-|11
77.247.181.163|lumumba.torservers.net|11
185.107.47.171|tor-exit.r2.darknet.dev|10
185.220.102.7|-|10
185.220.102.8|-|10
77.247.181.162|chomsky.torservers.net|10
178.165.72.177|178-165-72-177-kh.maxnet.ua|10
77.247.181.165|politkovskaja.torservers.net|10
195.206.105.217|zrh-exit.privateinternetaccess.com|10
185.100.87.206|geri.enn.lu|10
171.25.193.77|tor-exit1-readme.dfri.se|9
185.165.168.229|-|9
176.10.99.200|accessnow.org|9
144.217.255.89|ns542132.ip-144-217-255.net|9
95.211.230.211|-|9
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
185.100.87.207|freki.enn.lu|9
58.82.183.95|-|8
162.247.74.204|billsf.tor-exit.calyxinstitute.org|8
185.220.101.33|-|8
69.158.207.141|-|8
46.165.245.154|-|8
178.20.55.18|marcuse-2.nos-oignons.net|8
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|8
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|8
163.172.77.243|163-172-77-243.rev.poneytelecom.eu|8
45.33.70.146|ssh.scan.ampereinnotech.com|8
185.220.101.27|-|8
92.63.194.104|-|8
101.227.243.56|mail-cn.itls.asia|8
185.220.102.6|-|8
104.244.76.245|zarathustra.tor.k0nsl.org|8
78.131.11.10|-|8
176.10.104.240|tor1e1.digitale-gesellschaft.ch|8
185.220.101.28|-|8
167.88.7.134|the-windy-onion.tor-exits.alec.ninja|8
171.25.193.235|tor-exit3-readme.dfri.se|8
222.124.18.155|opted-out-dns2.telkom.net.id|8
171.25.193.20|tor-exit0-readme.dfri.se|8
171.25.193.25|tor-exit5-readme.dfri.se|8
80.67.172.162|algrothendieck.nos-oignons.net|8
94.230.208.147|tor3e1.digitale-gesellschaft.ch|8
45.148.10.143|-|8
107.189.11.193|-|8
195.176.3.19|tor4e1.digitale-gesellschaft.ch|8
5.199.130.188|tor.piratenpartei-nrw.de|8
104.244.76.13|tor-exit-node.spongebob.nicdex.com|8
104.244.78.197|mx.work.wf|8
144.91.68.122|vmi299127.contaboserver.net|8
185.220.101.34|-|8
158.174.122.199|h-122-199.A357.priv.bahnhof.se|8
