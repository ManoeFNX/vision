PHONECAM ALERT — REFONTE V10
============================================

Cette archive contient le site complet, avec une refonte graphique et des corrections fonctionnelles. Les modules du projet de départ ont été conservés : caméra PC/téléphone, liaison PeerJS, détection de mouvement, reconnaissance faciale, personnes enregistrées, alertes, médias et paramètres.

NOUVEAUTÉS / CORRECTIONS
------------------------
- Nouvelle interface responsive : navigation latérale, cartes, panneaux caméra, médiathèque, fiches personnes et paramètres harmonisés.
- Bascule entre apparence sombre et claire, avec mémorisation du choix.
- Amélioration de l'accessibilité clavier et de la lisibilité sur petits écrans.
- Les notifications/toasts et éléments d'événement affichent leur texte sans interpréter les noms ou détails comme du HTML.
- Chargement plus robuste des paramètres lorsque le stockage local est absent ou illisible.
- Le réglage « Détection de mouvement » met effectivement l'analyse en pause.
- Le délai entre alertes utilise le réglage « Délai entre alertes ».
- « Capture à chaque passage » active/désactive réellement les captures automatiques.
- Les réglages comportementaux (sensibilité, délai, capture et reconnaissance) sont transmis au téléphone connecté.
- La liaison utilise une sérialisation compatible avec les ArrayBuffer des captures automatiques.
- À l'arrêt ou à la déconnexion du flux vidéo, l'aperçu PC revient à l'état d'attente.
- Les réglages d'animations, d'effets lumineux et de mode compact ont un effet visuel réel.

FICHIERS
--------
index.html          Structure de toutes les vues de l'application
css/style.css       Nouvelle interface et règles responsive
js/storage.js       Paramètres et journal local
js/connection.js    Liaison PC / téléphone
js/camera.js        Capture vidéo, photos, audio et enregistrement
js/detection.js     Détection de mouvement
js/media.js         Médiathèque locale et migration des anciens médias
js/people.js        Gestion des personnes et photos de référence
js/recognition.js   Détection et comparaison faciale

LANCEMENT
---------
1. Décompresse le ZIP dans un dossier.
2. Ouvre le dossier dans VS Code ou un autre éditeur.
3. Lance index.html avec un serveur local (par exemple l'extension Live Server de VS Code) pour tester sur le PC.
4. Pour utiliser le téléphone comme caméra, héberge le site sur une adresse HTTPS accessible par le téléphone. Les navigateurs mobiles bloquent généralement l'accès caméra depuis une adresse HTTP locale de type http://192.168.x.x. « localhost » est autorisé sur l'appareil lui-même.
5. Garde la page PC ouverte, saisis le code affiché dans la page ouverte sur le téléphone, appuie sur « Connecter », puis sur « Démarrer la caméra ».

DÉPENDANCES ET CONFIDENTIALITÉ
------------------------------
- PeerJS et face-api.js sont chargés depuis des CDN externes. Une connexion Internet est nécessaire pour charger ces bibliothèques et les modèles de reconnaissance.
- Par défaut, PeerJS utilise un serveur public de signalisation pour établir la liaison. Le flux vidéo est transmis par WebRTC entre les appareils lorsque le réseau le permet ; le serveur de signalisation sert à coordonner la connexion.
- Les photos de référence, les fiches de personnes et les descripteurs faciaux sont conservés dans le stockage local du navigateur (IndexedDB). Les paramètres et le journal sont conservés dans localStorage. La suppression des données du navigateur peut les effacer.
- Les captures de la médiathèque sont également stockées localement dans le navigateur. Le navigateur peut refuser l'écriture si son stockage est plein ou désactivé.
- La reconnaissance faciale n'est pas infaillible. La qualité de la lumière, l'angle, la taille du visage et les photos de référence influencent les résultats. Vérifie manuellement une correspondance avant toute décision importante.
- Demande le consentement des personnes avant d'enregistrer leurs photos ou de les inclure dans un système de reconnaissance.

LIMITES À CONNAÎTRE
-------------------
- La caméra et le micro doivent être autorisés par le navigateur.
- Les pare-feu, les restrictions réseau ou l'absence de connectivité peuvent empêcher une liaison WebRTC.
- La disponibilité et le fonctionnement des CDN ne dépendent pas de cette archive.
