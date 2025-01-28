Rete: 192.168.1.0/24

Indirizzo di rete: 192.168.1.0
Il primo indirizzo dell'intervallo.
Non può essere assegnato a un dispositivo perché identifica l'intera rete.

Maschera di sottorete: /24:
Indica che i primi 24 bit della rete sono usati per identificare la rete, lasciando i restanti 8 bit per gli host.

Intervallo di indirizzi:
Gli indirizzi utilizzabili per i dispositivi (host) vanno da 192.168.1.1 a 192.168.1.254.

broadcast: 192.168.1.255:
E' usato per comunicazioni a tutti i dispositivi della rete.

Per conoscere poi l'indirizzo del gateway (ossia il punto do congiunzione tra rete locale e internet) posso usare il comando `ip route`:
Supponiamo per esempio di vedere `default via 192.168.1.254`.
Questo è il gateway!

Numero di host
Ci sono 256-3=254 indirizzi utilizzabili, sottraendo l'indirizzo di rete, quello di broadcast e il gateway.


Riassunto:
```
192.168.1.0 -> rete
192.168.1.[1-253] -> host
192.168.1.254 -> gateway
192.168.1.255 -> broadcast
```

DHCP
Il DHCP (Dynamic Host Configuration Protocol) non è un dispositivo, ma un protocollo di rete.
Il servizio DHCP viene fornito da un dispositivo o un server che è connesso alla rete.
E' una funzionalità o un servizio implementato su un dispositivo che fa parte della rete.

DNS
Il DNS (Domain Name System) non è un dispositivo, ma un sistema o un protocollo di rete.
Tuttavia, il servizio DNS è fornito da un server o un dispositivo collegato alla rete.
