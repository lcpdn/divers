```bash
loic@XXX:~$ dig 3718fa66e6.optimicdn.com @8.8.8.8

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> 3718fa66e6.optimicdn.com @8.8.8.8
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 39526
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;3718fa66e6.optimicdn.com.      IN      A

;; Query time: 5 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Wed May 10 15:34:34 CEST 2017
;; MSG SIZE  rcvd: 53
```


```bash
loic@XXX:~$ dig www.alerte-saip.gouv.fr @8.8.8.8

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> www.alerte-saip.gouv.fr @8.8.8.8
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 64072
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;www.alerte-saip.gouv.fr.       IN      A

;; Query time: 4039 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Wed May 10 15:47:14 CEST 2017
;; MSG SIZE  rcvd: 52
```
```bash
loic@cozy:~$ dig www.alerte-saip.gouv.fr @194.2.0.6

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> www.alerte-saip.gouv.fr @194.2.0.6
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33694
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 16
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.alerte-saip.gouv.fr.       IN      A

;; ANSWER SECTION:
www.alerte-saip.gouv.fr. 3600   IN      CNAME   2-01-48eb-0003.cdx.cedexis.net.

;; AUTHORITY SECTION:
net.                    61898   IN      NS      a.gtld-servers.net.
net.                    61898   IN      NS      j.gtld-servers.net.
net.                    61898   IN      NS      c.gtld-servers.net.
net.                    61898   IN      NS      h.gtld-servers.net.
net.                    61898   IN      NS      k.gtld-servers.net.
net.                    61898   IN      NS      g.gtld-servers.net.
net.                    61898   IN      NS      b.gtld-servers.net.
net.                    61898   IN      NS      m.gtld-servers.net.
net.                    61898   IN      NS      d.gtld-servers.net.
net.                    61898   IN      NS      i.gtld-servers.net.
net.                    61898   IN      NS      f.gtld-servers.net.
net.                    61898   IN      NS      e.gtld-servers.net.
net.                    61898   IN      NS      l.gtld-servers.net.

;; ADDITIONAL SECTION:
a.gtld-servers.net.     61897   IN      A       192.5.6.30
a.gtld-servers.net.     61897   IN      AAAA    2001:503:a83e::2:30
b.gtld-servers.net.     61897   IN      A       192.33.14.30
b.gtld-servers.net.     61897   IN      AAAA    2001:503:231d::2:30
c.gtld-servers.net.     61897   IN      A       192.26.92.30
d.gtld-servers.net.     61897   IN      A       192.31.80.30
e.gtld-servers.net.     61897   IN      A       192.12.94.30
f.gtld-servers.net.     61897   IN      A       192.35.51.30
g.gtld-servers.net.     61897   IN      A       192.42.93.30
h.gtld-servers.net.     61897   IN      A       192.54.112.30
i.gtld-servers.net.     61897   IN      A       192.43.172.30
j.gtld-servers.net.     61897   IN      A       192.48.79.30
k.gtld-servers.net.     61897   IN      A       192.52.178.30
l.gtld-servers.net.     61897   IN      A       192.41.162.30
m.gtld-servers.net.     61897   IN      A       192.55.83.30

;; Query time: 38 msec
;; SERVER: 194.2.0.6#53(194.2.0.6)
;; WHEN: Wed May 10 16:10:16 CEST 2017
;; MSG SIZE  rcvd: 581
```

```bash
loic@XXX:~$ dig SOA 3718fa66e6.optimicdn.com

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> SOA 3718fa66e6.optimicdn.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37948
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;3718fa66e6.optimicdn.com.      IN      SOA

;; ANSWER SECTION:
3718fa66e6.optimicdn.com. 360   IN      CNAME   2-01-48eb-0002.cdx.cedexis.net.

;; AUTHORITY SECTION:
2-01-48eb-0002.cdx.cedexis.net. 19 IN   SOA     flipa.cedexis.net. admin.cedexis.com. 1494429502 14400 7200 604800 19

;; Query time: 13 msec
;; SERVER: 62.210.16.6#53(62.210.16.6)
;; WHEN: Wed May 10 17:18:25 CEST 2017
;; MSG SIZE  rcvd: 153
```

