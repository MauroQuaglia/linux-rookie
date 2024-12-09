# Come funziona
Il servizio `systemd-resolved` è già incluso nella libreria `systemd` installta in Debian.

## I file in gioco
```
/etc/resolv.conf
/run/systemd/resolve/stub-resolv.conf
/etc/systemd/resolved.conf
```

## Spiegazione
* Normalmente quando si cerca di risolvere un indirizzo, vengono cercato i DNS nel file `etc/resolv.conf`.
* Se però voglio usare il servizio `systemd-resolved` devo creare un link simbolico da `etc/resolv.conf` a `/run/systemd/resolve/stub-resolv.conf`.
* Il file `/run/systemd/resolve/stub-resolv.conf` specificherà un`nameserver 127.0.0.53` che dice in sostanza che sto usando un servizio DNS locale sulla mia macchina.
* Il file di configurazione del servizio gli dirà poi qual è il DNS.


# Riassumendo
* Primo passo:
  * `/etc/systemd/resolved.conf`
  * La configurazione del servizio che contiene i DNS: `DNS=8.8.8.8 1.1.1.1`

* Secondo passo:
  * `/etc/resolv.conf -> /run/systemd/resolve/stub-resolv.conf`

* Terzo passo
  * Riavviare il servizio.
  * Il file `/run/systemd/resolve/stub-resolv.conf` non è da editare, viene creato in automatico in base ai valori configurati in `/etc/systemd/resolved.conf`.