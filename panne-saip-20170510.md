J'ai fait un petit bot Twitter qui tweete en cas de déclenchement d'une alerte sur l'application SAIP. Et aujourd'hui, patatra, vala que le bot tweete de manière erratique. La façon (sale) dont je l'avais codé me laisse à penser que les serveurs mettant à disposition les infos sont mal en point. En effet, impossible de les contacter, la fameuse erreur "Name not resolved" frappe. Alors faisons un petit dig sur les serveurs du projet Google Public DNS pour essayer d'avoir une résolution comme le ferait un client standard:
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
En gros: rien et rien. Il est impossible d'avoir une résolution DNS (celle associant le FQDN à l'adresse IP). En essayant d'interroger en remontant la chaîne de serveurs DNS:

```bash
loic@XXX:~$ dig SOA www.alerte-saip.gouv.Fr

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> SOA www.alerte-saip.gouv.Fr
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20394
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.alerte-saip.gouv.Fr.       IN      SOA

;; ANSWER SECTION:
www.alerte-saip.gouv.Fr. 3600   IN      CNAME   2-01-48eb-0003.cdx.cedexis.net.

;; AUTHORITY SECTION:
2-01-48eb-0003.cdx.cedexis.net. 19 IN   SOA     flipa.cedexis.net. admin.cedexis.com. 1494430313 14400 7200 604800 19

;; Query time: 24 msec
;; SERVER: 62.210.16.6#53(62.210.16.6)
;; WHEN: Wed May 10 17:31:56 CEST 2017
;; MSG SIZE  rcvd: 155
```
On découvre que le serveur qu'il tente de joindre est un CNAME d'un host d'un sous-domaine de cedexis. Et que les serveurs DNS permettant la résolution en question sont aussi des serveurs de Cedexis. Bref, que tous les oeufs sont dans le même panier.
En tentant la même opération sur l'host hébergeant la liste des alertes:
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
Même résultat, l'host est un CNAME d'un Host de Cedexis.

Or, Cedexis est victime d'une attaque aujourd'hui. Ses réseaux sont (globalement) injoignable. Et SAIP ne fonctionne donc pas.
