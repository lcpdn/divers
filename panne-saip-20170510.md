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
