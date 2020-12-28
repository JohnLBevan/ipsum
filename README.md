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
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2020-12-28)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
31.220.1.233|-|10
51.83.187.201|vps-cebd8d8e.vps.ovh.net|10
145.239.92.26|relay3.tor.ian.sh|10
31.220.0.202|battle-scape.com|10
185.220.102.245|185-220-102-245.torservers.net|9
185.220.102.246|185-220-102-246.torservers.net|9
185.220.102.240|185-220-102-240.torservers.net|9
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|9
31.220.2.107|dedicated.koddos.com|9
45.154.168.201|ip.201.168.154.45.as208196.net|9
31.220.0.249|-|9
178.165.72.177|178-165-72-177-kh.maxnet.ua|9
31.220.1.169|opdoek.ricetell.com|9
62.102.148.68|-|9
198.251.83.248|tor-exit-02.nonanet.net|9
171.25.193.78|tor-exit4-readme.dfri.se|9
185.220.101.1|-|9
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|9
171.25.193.25|tor-exit5-readme.dfri.se|9
185.220.101.208|-|9
107.189.10.27|-|8
31.220.3.147|dedicated.koddos.com|8
31.220.3.148|dedicated.koddos.com|8
31.220.0.203|ultrablockparty.com|8
217.182.78.180|vps-0695db4d.vps.ovh.net|8
54.38.81.231|ns31251136.ip-54-38-81.eu|8
185.220.102.244|185-220-102-244.torservers.net|8
185.220.102.243|185-220-102-243.torservers.net|8
45.154.168.147|ip.147.168.154.45.as208196.net|8
145.239.82.168|vps-04c383fd.vps.ovh.net|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
104.244.73.13|LuxembourgTorExit1|8
45.154.35.221|45-154-35-221.v4.as52042.net|8
185.220.101.193|-|8
162.247.74.27|turing.tor-exit.calyxinstitute.org|8
54.38.52.137|vps-13c8a062.vps.ovh.net|8
104.244.72.168|LuxembourgTor7.lu|8
104.244.73.205|LuxembourgTor5.lu|8
145.239.95.15|tor-exit.nightmare.life|8
185.56.80.65|xx.freeflux.org|8
45.154.35.222|45-154-35-222.v4.as52042.net|8
62.102.148.69|-|8
51.158.111.157|157-111-158-51.instances.scw.cloud|8
185.191.124.152|-|8
31.220.2.222|-|8
31.220.1.170|cgunw.ricetell.com|8
91.192.103.10|-|8
91.192.103.15|-|8
171.25.193.77|tor-exit1-readme.dfri.se|8
45.154.35.216|45-154-35-216.v4.as52042.net|8
45.154.35.219|45-154-35-219.v4.as52042.net|8
23.129.64.216|-|8
145.239.82.142|vps-a153c854.vps.ovh.net|8
77.247.181.162|chomsky.torservers.net|8
193.218.118.95|95.118.218.193.urdn.com.ua|8
171.25.193.20|tor-exit0-readme.dfri.se|8
23.129.64.197|-|8
104.244.74.121|LuxembourgTor4|8
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|8
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|8
91.192.103.24|-|8
185.220.101.198|-|8
185.220.101.194|-|8
185.32.222.171|-|8
31.220.2.108|dedicated.koddos.com|8
51.68.143.212|vps-6bc10a92.vps.ovh.net|8
51.83.129.84|relay15f.tor.ian.sh|7
49.235.113.90|-|7
122.55.190.12|122.55.190.12.static.pldt.net|7
107.170.227.141|-|7
195.154.179.3|195-154-179-3.rev.poneytelecom.eu|7
221.181.185.36|-|7
185.220.102.247|185-220-102-247.torservers.net|7
185.220.102.241|185-220-102-241.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
218.93.207.40|-|7
51.83.134.17|vps-a84eaf66.vps.ovh.net|7
91.192.103.34|-|7
203.177.71.254|-|7
145.239.82.229|vps-45ff0b03.vps.ovh.net|7
31.220.0.186|padbanking.net|7
23.129.64.203|-|7
217.170.205.14|tor-exit-5014.nortor.no|7
81.70.23.139|-|7
159.203.74.227|mnc.pw.development|7
177.131.11.190|177-131-11-190.netfacil.center|7
193.218.118.213|213.118.218.193.urdn.com.ua|7
198.144.120.234|-|7
43.240.102.4|-|7
138.68.236.50|-|7
185.220.101.139|-|7
185.220.102.6|185-220-102-6.torservers.net|7
198.98.50.112|tor.your-domain.tld|7
138.197.143.146|-|7
51.77.135.89|ns31066279.ip-51-77-135.eu|7
104.244.73.93|LuxembourgTor3|7
205.185.127.217|tor-exit.monoxyde.org|7
185.67.82.114|tor-ou.effi.org|7
101.71.51.192|-|7
51.75.144.43|ns3129517.ip-51-75-144.eu|7
104.244.76.13|tor-exit-node.spongebob.nicdex.com|7
222.187.222.55|-|7
45.154.35.220|45-154-35-220.v4.as52042.net|7
2.57.122.163|-|7
185.220.100.240|tor-exit-13.zbau.f3netze.de|7
23.129.64.189|-|7
107.189.10.251|-|7
195.206.105.217|zrh-exit.privateinternetaccess.com|7
51.77.58.144|vps-aba9cb06.vps.ovh.net|7
51.75.64.187|relay4.tor.ian.sh|7
89.234.157.254|marylou.nos-oignons.net|7
51.210.80.127|tor-exit-fr.letztermensch.com|7
185.191.124.150|-|7
91.192.103.11|-|7
91.192.103.16|-|7
167.88.7.134|the-windy-onion.tor-exits.alec.ninja|7
45.154.35.217|45-154-35-217.v4.as52042.net|7
45.154.35.214|45-154-35-214.v4.as52042.net|7
23.129.64.217|-|7
31.220.40.241|-|7
213.164.204.3|h-213-164-204-3.NA.cust.bahnhof.se|7
185.220.101.24|-|7
185.220.101.22|-|7
209.141.41.103|tor-relay-3.mnpnk.com|7
31.220.40.238|-|7
185.220.102.8|185-220-102-8.torservers.net|7
193.218.118.235|235.118.218.193.urdn.com.ua|7
77.247.181.165|politkovskaja.torservers.net|7
46.101.40.21|-|7
213.61.215.54|-|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
106.52.231.46|-|7
107.189.10.246|-|7
176.10.99.200|accessnow.org|7
198.144.120.177|-|7
185.117.119.189|unknowhekker1.example.com|7
31.220.40.163|-|7
91.121.91.82|ns3032781.ip-91-121-91.eu|7
45.155.205.86|-|7
45.155.205.87|-|7
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|7
119.28.51.99|-|7
91.192.103.25|-|7
91.192.103.26|-|7
5.199.130.188|tor.piratenpartei-nrw.de|7
185.32.222.172|-|7
193.239.232.101|-|7
51.75.52.118|ns3130898.ip-51-75-52.eu|7
185.220.101.207|-|7
185.220.101.202|-|7
51.195.148.18|relay2.tor.ian.sh|7
165.227.132.233|-|7
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|7
185.220.101.146|-|7
185.220.101.206|-|7
193.218.118.243|243.118.218.193.urdn.com.ua|7
185.100.87.207|freki.enn.lu|7
