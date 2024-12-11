# Osservazione
* Utile per vedere dipendenze&C.: `sudo apt show xxx`
* Sia `DPKGL=dpkg -l | egrep 'lynx|lynx_common|libidn11' --color`

----
# APT 
* Metodo ufficiale e meno problematico quando devo disinstallare.

* `DPKGL`: non c'è nulla  
* `sudo apt install lynx -y`
* `DPKGL`: ci sono tutte e tre
* `sudo apt purge lynx -y`: toglie `lynx` ma lascia le dipendenze!
* `DPKGL`: ci sono le dipendenze
* `sudo apt autoremove --purge -y`: butta anche le dipendenze
* `DPKGL`: pulito!

----
# DPKG  
* Per installare librerie "manualmente" da repository o vendor non ufficiali.
* Più problematico quando voglio fare pulizia perché lascia dipendenze in giro.

* `DPKGL`: non c'è nulla
* `sudo apt install --download-only lynx -y`
  * Guardo in `/var/cache/apt/archives/` e vedo le tre librerie con estensione `.deb`.
* Allora gli installo le dipendenze e poi la libreria principale.
  * `sudo dpkg -i libidn11_1.33-3_amd64.deb`
  * `sudo dpkg -i lynx-common_2.9.0dev.6-3~deb11u1_all.deb`
  * `sudo dpkg -i lynx_2.9.0dev.6-3~deb11u1_amd64.deb`
* `DPKGL`: ci sono tutte e tre
* `sudo apt purge lynx -y`: toglie `lynx` ma lascia le dipendenze!
* `DPKGL`: ci sono le dipendenze
* `sudo apt autoremove --purge -y`: __NON__ butta le dipendenze
* `DPKGL`: rimangono le due dipendenze!

----
# Compilazione di codice sorgente
* Complesso e difficile da gestire.

* Riporto un esempio:
* `sudo apt install build-essential -y`: per installare le librerie utili per la compilazione.
* `wget https://invisible-mirror.net/archives/lynx/tarballs/lynx2.8.9rel.1.tar.gz`
* `tar zxvf lynx2.8.9rel.1.tar.gz`
* `cd lynx2.8.9rel.1/`
* `./configure`: fa un check ed eventualmente richiede di installare alcune dipendenze, tipo `libncurses5-dev` e `libncursesw5-dev`.
* `sudo apt install libncurses5-dev libncursesw5-dev -y`
* `./configure`: ora tutto OK
* `make`
* `sudo make install`
* `make clean`

* Se poi voglio disinstallare:
* `sudo make uninstall`

* Tuttavia per ogni libreria che compilo devo leggermi i vari README e guide all'interno dei file scaricati per sapere cosa fare.

---

# Riassumento
* Se installo con `apt` è poi facile rimuovere con una combinazione di `sudo apt purge xxx -y` + `sudo apt autoremove --purge -y`.
* Se installo con `dpkg` poi diventa un problema rimuovere le dipendenze.
* Se compilo il codice sorgente diventa un po' un casino, meglio non farlo.
