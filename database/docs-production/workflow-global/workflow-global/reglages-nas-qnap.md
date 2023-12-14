# Réglages NAS QNAP

[https://www.youtube.com/watch?v=-cSUPRVmqng](https://www.youtube.com/watch?v=-cSUPRVmqng)

[https://www.youtube.com/watch?v=XGXN6f7DvTI](https://www.youtube.com/watch?v=XGXN6f7DvTI)

[https://www.youtube.com/watch?v=a5a8Fdz3ukY](https://www.youtube.com/watch?v=a5a8Fdz3ukY)

Voici un résumé de la vidéo:

Damon Cooper présente le NAS TS-453BT3 de QNAP, un système de stockage en réseau qui permet à plusieurs utilisateurs d'éditer des vidéos 4K RAW simultanément via Ethernet 10 Gbit/s ou Thunderbolt. Il explique que lui et sa collègue Belle ont besoin d'accéder aux mêmes fichiers vidéo en même temps pour monter différents projets.

Le TS-453BT3 offre 4 baies pour des disques durs, 2 ports Thunderbolt 3, 2 ports Ethernet 1 Gbit/s et 1 port Ethernet 10 Gbit/s. Bien qu'annoncé comme un DAS, les ports Thunderbolt fonctionnent en fait comme de l'Ethernet, donc chaque ordinateur y accède via une adresse IP différente.

Les tests montrent 300 Mo/s en lecture et écriture via Thunderbolt avec le protocole NFS Final Cut. Avec SMB sur Thunderbolt, 600 Mo/s en lecture et 250 Mo/s en écriture. Sur Ethernet 10 Gbit/s, 600 Mo/s en lecture, 250 Mo/s en écriture. Damon montre qu'on peut lire 2 flux 4K RAW multicam simultanément.

Le TS-453BT3 offre de nombreuses fonctionnalités logicielles mais son espace disque limité a poussé Damon à construire son propre serveur. Néanmoins, le TS-453BT3 est une excellente solution abordable pour les petites équipes.

Voici quelques détails supplémentaires sur la vidéo :

- Damon explique que le TS-453BT3 permet à deux ordinateurs d'être connectés en Thunderbolt 3 simultanément, ce qui est rare pour ce type d'appareil. Chaque ordinateur obtient une adresse IP différente.
- Pour les protocoles réseau, il recommande d'utiliser NFS optimisé pour Final Cut en Thunderbolt (300Mo/s en lecture/écriture), ou SMB en Thunderbolt (600Mo/s en lecture, 250Mo/s en écriture) ou NFS classique en 10Gbit Ethernet (600Mo/s en lecture).
- Il a testé la lecture de 2 flux 4K RAW à 1 Gbit/s en multicam, soit 250 Mo/s de débit total, sans problème en Thunderbolt et 10Gbit Ethernet.
- Le TS-453BT3 offre de nombreuses fonctionnalités logicielles natives comme sauvegarde, gestion de stockage, serveur web distant, mais Damon n'en a pas exploité le potentiel.
- Damon a remplacé le TS-453BT3 par un serveur DIY avec plus d'espace disque. Le TS-453BT3 reste une bonne option abordable pour les petites équipes jusqu'à 2 monteurs simultanés.
- Il n'a pas testé sous Windows mais pense que les performances réseau devraient être encore meilleures comparé à Mac.

Configurer les adresses IP de votre QNAP TS-453BT3 via l'interface web. Assurez-vous que votre QNAP est connecté au réseau via le port Thunderbolt 3 et que votre MacBook Air est également connecté au même réseau. Voici les étapes générales pour configurer les adresses IP :

1. **Trouver l'adresse IP actuelle du QNAP :**
    - Sur le QNAP, il devrait y avoir un écran LCD ou un affichage LED qui affiche l'adresse IP actuelle. Si vous ne voyez pas cette information, vous pouvez essayer d'utiliser un outil de scan de réseau pour trouver l'adresse IP attribuée à votre QNAP.
2. **Accéder à l'interface web du QNAP :**
    - Ouvrez un navigateur Web sur votre MacBook Air.
    - Entrez l'adresse IP actuelle du QNAP dans la barre d'adresse du navigateur et appuyez sur Entrée. Cela devrait vous amener à la page de connexion de l'interface web de l'appareil QNAP.
3. **Connectez-vous à l'interface web :**
    - Entrez vos informations d'identification (nom d'utilisateur et mot de passe). Si vous ne les avez pas encore configurées, utilisez les informations par défaut (généralement "admin" pour le nom d'utilisateur et "admin" pour le mot de passe).
4. **Accéder aux paramètres réseau :**
    - Une fois connecté, recherchez les paramètres réseau. Ils peuvent être sous l'onglet "Réseau" ou "Configuration du réseau".
5. **Configurer l'adresse IP :**
    - Vous devrez probablement changer les paramètres IP de votre QNAP de "Dynamique" (DHCP) à "Statique" (adresse IP fixe) pour pouvoir configurer manuellement l'adresse IP.
    - Entrez les informations suivantes :
        - Adresse IP : L'adresse IP que vous souhaitez attribuer au QNAP (assurez-vous qu'elle est dans le même sous-réseau que votre MacBook Air).
        - Masque de sous-réseau : Cela définit la portée de votre réseau.
        - Passerelle par défaut : L'adresse IP du routeur de votre réseau.
        - Serveur DNS : Les adresses IP des serveurs DNS de votre FAI ou des serveurs DNS publics comme ceux de Google (8.8.8.8, 8.8.4.4).
6. **Enregistrez les paramètres :**
    - Après avoir entré les informations, enregistrez les modifications. Le QNAP peut nécessiter un redémarrage pour appliquer les nouveaux paramètres.
7. **Vérification de la connectivité :**
    - Assurez-vous que le QNAP est accessible via l'adresse IP que vous avez configurée. Vous devriez pouvoir y accéder via le navigateur en utilisant la nouvelle adresse IP.

N'oubliez pas que ces instructions sont basées sur des généralités, et l'interface exacte et les options peuvent varier en fonction de la version du firmware de votre QNAP. Si vous avez des doutes ou des inquiétudes, il est recommandé de consulter le manuel d'utilisation spécifique à votre modèle QNAP ou de contacter le support technique de QNAP pour obtenir une assistance personnalisée.

[https://www.qnap.com/en/product/qsw-1208-8c](https://www.qnap.com/en/product/qsw-1208-8c)

ONDULEUR 

[APC Power-Saving Back-UPS PRO - BR1500G-FR - Onduleur 1500VA (AVR, 6 Prises FR, USB, Logiciel d'arrêt)](https://www.amazon.fr/APC-Power-Saving-Back-UPS-PRO-BR900G-FR/dp/B004FOVYG6/ref=sr_1_5?__mk_fr_FR=ÅMÅŽÕÑ&keywords=APC+UPS+1350VA&sr=8-5&th=1)

[APC Power-Saving Back-UPS PRO - BR1500G-FR - Onduleur 1500VA (AVR, 6 Prises FR, USB, Logiciel d'arrêt)](https://www.amazon.fr/APC-Power-Saving-Back-UPS-PRO-BR900G-FR/dp/B004FOVYG6/ref=sr_1_5?__mk_fr_FR=ÅMÅŽÕÑ&keywords=APC+UPS+1350VA&sr=8-5&th=1)