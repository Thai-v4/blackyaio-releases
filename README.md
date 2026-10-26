# Installer blackyaio

Ce guide est pour toi si tu installes l'app. Pas de terminal ni de fichier à modifier : tout se règle dans l'app.

blackyaio surveille poliment trois boutiques (King Jouet, JouéClub, King'Dultes), t'alerte sur Discord et prépare ton panier. **Tu paies toujours toi-même**, dans ton navigateur. Ta copie est à toi : tes réglages, tes alertes et tes profils restent sur ton ordinateur.

## Où le télécharger

Toutes les versions sont sur [github.com/Thai-v4/blackyaio-releases](https://github.com/Thai-v4/blackyaio-releases/releases/latest). Ouvre la dernière, puis, sous « Assets », prends le fichier de ton ordinateur :

| Ton ordinateur | Fichier |
|---|---|
| Mac (puce Apple ou Intel), macOS 13 ou plus récent | `blackyaio-<version>-mac.dmg` |
| Windows 10 ou 11, 64 bits | `blackyaio-<version>-windows.exe` |
| Linux Ubuntu ou Debian, PC classique | `blackyaio_<version>_amd64.deb` |
| Linux Ubuntu ou Debian, puce Arm (Raspberry Pi…) | `blackyaio_<version>_arm64.deb` |
| Autre Linux, PC classique | `blackyaio-<version>-linux-x86_64.AppImage` |

Les autres fichiers (`latest….yml`, `….blockmap`) servent aux mises à jour : ne les ouvre pas.

## Mac

1. Ouvre le `.dmg`, puis glisse **blackyaio** sur le dossier **Applications**.
2. Ouvre blackyaio depuis Applications. La première fois, macOS refuse : l'app n'est pas signée par un développeur enregistré chez Apple. Ferme ce message (sans mettre l'app à la corbeille).
3. Ouvre **Réglages Système › Confidentialité et sécurité**, descends jusqu'au message sur blackyaio et clique sur **Ouvrir quand même**, puis confirme avec ton mot de passe ou Touch ID.

C'est à refaire à chaque nouvelle version. Les libellés exacts peuvent varier selon ta version de macOS.

## Windows

1. Lance `blackyaio-<version>-windows.exe`. Si ton navigateur prévient que ce fichier est peu téléchargé, choisis de le conserver.
2. Windows affiche « Windows a protégé votre ordinateur » (SmartScreen), car l'installeur n'est pas signé. Clique sur **Informations complémentaires**, puis sur **Exécuter quand même**.
3. L'installation se fait seule, sans droits d'administrateur, et l'app s'ouvre à la fin. Elle crée un raccourci sur le Bureau et dans le menu Démarrer.

## Linux

- **Ubuntu ou Debian** : ouvre le `.deb` avec ta logithèque (double-clic), ou installe-le avec `sudo apt install ./blackyaio_<version>_amd64.deb` (`arm64` sur une puce Arm). Le paquet règle aussi ce qu'il faut au bac à sable de l'app, dont un profil AppArmor sous Ubuntu 24.04 et suivants.
- **Autre distribution** : rends l'AppImage exécutable (Propriétés › Permissions › « Autoriser l'exécution comme programme »), puis double-clique. Certaines distributions demandent FUSE 2 (paquet `libfuse2` ou `fuse2`). Sous Ubuntu 24.04 et suivants, prends plutôt le `.deb` : l'AppImage risque de ne pas démarrer (restrictions d'AppArmor).

## Premier lancement

L'écran vide liste les premiers pas, chacun avec son bouton « Régler… » :
1. **Alertes Discord** : colle l'adresse du webhook de ton serveur Discord, puis envoie un message de test ;
2. **Profil d'agent King'Dultes** : « Utiliser le profil public du projet » suffit ;
3. **Profil de livraison** (facultatif) : il pré-remplit le panier King'Dultes. Il est chiffré par une phrase de passe que toi seul connais.

Ajoute ensuite une fiche avec **Nouvelle tâche**, puis démarre la surveillance.

## Mises à jour

L'app cherche une nouvelle version au démarrage, puis toutes les 6 heures. Elle demande seulement à GitHub la liste des versions et leurs fichiers ; elle n'y envoie rien de toi (ni réglage, ni identifiant de ta copie). GitHub voit ton adresse IP, comme pour n'importe quel téléchargement. L'état est sous **Mises à jour**, en bas de la barre latérale, qui passe en bleu quand une version t'attend.

- **Windows et AppImage** : la nouvelle version se télécharge seule. Clique sur **Redémarrer pour mettre à jour**, ou ferme simplement l'app : elle s'installe à la fermeture.
- **Linux (`.deb`)** : la nouvelle version se télécharge seule ; **Redémarrer pour mettre à jour** te demande ton mot de passe, car c'est l'installation d'un paquet. Rien ne s'installe sans ce clic.
- **Mac** : macOS refuse qu'une app sans signature Apple se remplace seule. L'app te prévient et **Télécharger la version…** ouvre le téléchargement : glisse la nouvelle version dans Applications, remplace l'ancienne, puis refais « Ouvrir quand même ».
- **Jamais de redémarrage surprise** : si la surveillance tourne quand tu cliques, l'app te demande d'abord ; elle s'arrête le temps de l'installation et reprend seule ensuite.
- Tes réglages, tes tâches et tes profils restent à chaque mise à jour.
- Copie installée avant le 26/10/2026 (fichier reçu à la main) : elle ne sait pas se mettre à jour. Installe une fois la dernière version du dépôt par-dessus ; la suite se fera seule (ou avec un avis, sur Mac).

## Au quotidien

- **Fermer la fenêtre quitte l'app.** Si la surveillance tourne, l'app te demande d'abord, car une fois l'app fermée, plus aucune vérification ni alerte n'a lieu. Les jours de sortie, garde-la ouverte.
- **Tes données** (réglages, tâches, profils chiffrés) sont rangées ici :
  - Mac : `~/Library/Application Support/blackyaio`
  - Windows : `%APPDATA%\blackyaio`
  - Linux : `~/.config/blackyaio`

  Désinstaller l'app ne les efface pas. Le fichier `.env` de ce dossier contient ton webhook Discord : ne le partage jamais.
