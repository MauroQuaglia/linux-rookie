# Sono xpuser e voglio eseguire un comando come root senza sapere la password di root
* Se sono nei sudoers per cmd: `sudo [cmd]` (`sudo -u xpuser [cmd]`)
* Altrimenti provo a diventare root e poi a eseguire il comando: `sudo su - root` (`sudo -u xpuser su - root`)

# Creazione di un utente (esempi)
* Il `man adduser` è sempre illuminante.
* `adduser` -> più interattivo e user friendly.
  *  `adduser --gid 2000 --disabled-password --gecos "Pippo User" pippo`
* `useradd` -> di basso livello, più potente e compatibile, non user friendly.
* In docker dove non vogliamo cose interattive è meglio usare `useradd` (`man useradd`)
  * Per esempio: `useradd --comment "Docker User" --uid 3001 --gid 2000 --create-home --shell /bin/bash dockeruser`
  * Posso anche non mettere la password, devo decidere. La password serve per accedere, ma se devo lanciare uno script dall'utente dockeruser lo posso fare.
  * Poi eventualmente da root posso diventare utente dockeruser se mi serve.
* Altro esempio minimale: 
  * `useradd --uid 3003 --gid 2000 xio`
  * Non ho ne home, ne password, infatti in `/etc/shadow` c'è `xio:!:...`