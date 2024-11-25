# Sono xpuser e voglio eseguire un comando come root senza sapere la password di root
* Se sono nei sudoers per cmd: `sudo [cmd]` (`sudo -u xpuser [cmd]`)
* Altrimenti provo a diventare root e poi a eseguire il comando: `sudo su - root` (`sudo -u xpuser su - root`)