# Come funziona
* Il servizio `sshd` è costituito dalla parte __client__ e da quella __server__.
* Di solito il __client__ è già installato di default.
* Il __server__ è da installare se serve.

## I file in gioco
```
/etc/ssh/sshd_config
```

## Un esempio di creazione utente
* Sulla macchina Vagrant:
  * `sudo su - root`
  * `useradd -m -s /bin/bash mauro-vag`
  * `passwd mauro-vag` -> apevag
* Sulla macchina Locale:
  * `sudo su - root`
  * `userdel -r mauro-oct` (-r = remove home) (lo faccio nel caso esistesse già)
  * `useradd -m -s /bin/bash mauro-oct`
  * `passwd mauro-oct` -> apeoct
  * `su - mauro-oct`
  * `ssh-keygen -t rsa`
  * `ssh-copy-id mauro-vag@192.168.56.11`
    * Giustamente se nel file `/etc/sshd_config` ho `PasswordAuthentication no` non ci riesco.
    * Quindi faccio un giro di ansible con `PasswordAuthentication yes`, copio la chiave con `ssh-copy-id mauro-vag@192.168.56.11` che mi chiederà la password di `mauro-vag` e così la mia chiave pubblica di `mauro-oct` verrà copiata nelle `authorized_keys` di `mauro-vag` sulla macchina Vagrant.
    * A questo punto posso fare un altro giro di ansible con `PasswordAuthentication no`.
  * `ssh mauro-vag@192.168.56.11`: funziona!
