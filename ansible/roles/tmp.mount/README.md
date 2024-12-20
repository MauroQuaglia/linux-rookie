# Monto un filesystem tmpfs (che usa la RAM e non il disco) su una directory
* `mkdir tmpmq`
* `sudo mount -t tmpfs -o size=1G tmpfs /tmpmq`
* `mount | grep mq`
* `df -h /tmpmq/`
```
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.0G     0  1.0G   0% /tmpmq
```
# Servizio
* Posso anche gestire il tutto come servizio.

# tmp.mount
* Cerco tra i file https://github.com/systemd/systemd/tree/main/units.
* Questi file vengono forniti da Systemd e possono essere utilizzati per configurare e controllare i servizi sul tuo sistema Linux
* Mi prendo il https://github.com/systemd/systemd/blob/main/units/tmp.mount per il servizio che voglio installare.