* Aggiornare: `apt update`

* Installare da repository:
  * Si usa `apt`: 
  * `apt install lynx`

* Disinstallare 
  * `apt purge lynx` (rimuove `lynx` ma non le sue dipendenze)
  * `apt autoremove --purge lynx` (rimuove anche le dipendenze)

----
  
* Installare da vendor:
  * Si usa `dpkg`:
  * `sudo apt install --download-only lynx`
    * Guardo in `/var/cache/apt/archives/` e vedo le tre librerie con estensione `.deb`.
  * `sudo dpkg -i lynx_2.9.0dev.6-3~deb11u1_amd64.deb`: si arrabbia perché dice che vuole prima le dipendenze.
  * Allora gli installo le dipendenze e poi la libreria principale.
    * `sudo dpkg -i libidn11_1.33-3_amd64.deb`
    * `sudo dpkg -i lynx-common_2.9.0dev.6-3~deb11u1_all.deb`
    * `sudo dpkg -i lynx_2.9.0dev.6-3~deb11u1_amd64.deb`





