# Maintenance informatique win10 + Mac OSX

### Pour faire des backups projet sur Notion a des limites de taille de fichier qui dépendent du plan que vous utilisez :

- Pour les utilisateurs du plan gratuit, la limite de taille de fichier est de 5 Mo par fichier.
- Pour les utilisateurs des plans payants, la limite de taille de fichier est de 1000 Mo (soit 1 Go) par fichier.

Il est important de noter que les fichiers hébergés dans Notion contribuent à l'espace de stockage total de votre compte, qui est également limité en fonction du plan que vous utilisez. Si vous atteignez la limite d'espace de stockage de votre compte, vous devrez soit supprimer des fichiers existants, soit passer à un plan supérieur pour augmenter votre limite d'espace de stockage.

Il est donc important de vérifier les limites de taille de fichier et d'espace de stockage pour votre plan Notion avant de télécharger des fichiers volumineux. Si vous avez besoin d'uploader des fichiers de grande taille, il est recommandé d'utiliser des services de stockage de fichiers en ligne tels que Dropbox, Google Drive ou OneDrive, et de lier ces fichiers dans Notion plutôt que de les uploader directement dans Notion.

Here are the Notion plans and their respective total storage limits:

1. Personal Plan - 1000 blocks, 5MB maximum file upload size, and 1000 blocks of file storage.
2. Team Plan - unlimited blocks, 5MB maximum file upload size, and 1000 blocks of file storage per member.
3. Enterprise Plan - unlimited blocks, no maximum file upload size limit, and custom storage limits.

It's important to note that the storage limits for the Personal and Team plans include all types of content, including pages, databases, and files. If you reach the storage limit of your account, you will need to either delete existing content or upgrade to a higher plan to increase your storage limit.

### Cloner un disque système sur Windows 10 avec Acronis Cyber Protection

1. Ouvrir Acronis Cyber Protection et sélectionner "Clonage de disque" dans le menu principal.
2. Sélectionner le disque source que vous souhaitez cloner.
3. Sélectionner le disque cible qui est déjà installé dans l'ordinateur.
4. Cocher l'option "Utiliser le disque cible comme disque système".
5. Suivre les instructions à l'écran pour terminer le processus de clonage.

### Cloner un disque source pour un autre ordinateur avec du matériel similaire

1. Effectuer les étapes 1 à 4 ci-dessus.
2. Éjecter le disque cible de l'ordinateur source et l'installer dans l'ordinateur de destination.
3. Démarrer l'ordinateur de destination et vérifier que le clonage s'est terminé avec succès.

### Cloner un disque source pour un autre ordinateur avec du matériel différent implique l'utilisation de la fonctionnalité Universal Restore d'Acronis Cyber Protection. Voici les étapes à suivre :

1. Résumé de la procédure de restauration sur du matériel différent :
2. Valider la sauvegarde que vous souhaitez restaurer (pour toutes les sauvegardes sauf celles stockées dans Acronis Cloud).
3. Préparer les pilotes nécessaires.
4. Créer un support de démarrage Acronis Bootable Media avec l'outil Universal Restore d'Acronis. Vous aurez besoin de ce support pour restaurer votre système à partir de la sauvegarde et appliquer Universal Restore par la suite pour rendre votre ancien système amorçable sur le nouveau matériel.
5. Connecter le support de démarrage Acronis Bootable Media à votre ordinateur et redémarrer l'ordinateur. Restaurer votre système.
6. Après la restauration, redémarrer votre nouvel ordinateur et utiliser Universal Restore pour rendre le système restauré amorçable sur le nouveau matériel.
7. Maintenant, vous pouvez démarrer l'ordinateur et travailler avec votre système restauré sur le nouveau matériel.

Il est important de noter que vous devez préparer les pilotes nécessaires avant de créer le support de démarrage Acronis Bootable Media. Vous pouvez également utiliser un outil tel que "Driver Easy" pour identifier les pilotes manquants et les télécharger automatiquement. En outre, il est recommandé de valider la sauvegarde avant de procéder à la restauration pour éviter des problèmes éventuels.

1. help :

[](https://kb.acronis.com/ati2024/aur?ckattempt=1)

### Faire des backups des données et mettre en place une routine quotidienne

1. Ouvrir Acronis Cyber Protection et sélectionner l'option "Backup".
2. Sélectionner les fichiers et dossiers que vous souhaitez sauvegarder.
3. Configurer les options de backup, y compris la fréquence et l'emplacement de sauvegarde.
4. Cliquer sur "Démarrer le backup" pour lancer le processus de backup.

### En cas de disque système endommagé

1. Créer une clé USB de secours en utilisant l'option "Créer une clé USB de secours" dans Acronis Cyber Protection.
2. Insérer la clé USB de secours dans l'ordinateur endommagé et démarrer l'ordinateur à partir de la clé USB.
3. Suivre les instructions à l'écran pour réparer ou restaurer le disque système endommagé.

### Installation  de Windows 10 depuis une clé préparée (méthode normale depuis 0)

Rufus et les outils de création de supports d'installation intégrés à Windows (comme l'outil Media Creation Tool de Microsoft) ont chacun leurs avantages et leurs cas d'utilisation spécifiques. Voici une comparaison pour vous aider à décider quel outil est le meilleur pour vous :

**Rufus :**

- **Avantages :**
    - Peut être plus rapide pour créer des médias d'installation.
    - Offre des options avancées de personnalisation telles que le système de fichiers, le schéma de partition, etc.
    - Peut être utilisé pour créer des supports amorçables pour différents systèmes d'exploitation.
- **Cas d'utilisation :**
    - Idéal pour créer rapidement des supports d'installation amorçables personnalisés à partir d'images ISO.

**Outils de création de supports Windows (Media Creation Tool) :**

- **Avantages :**
    - Fourni directement par Microsoft, ce qui peut garantir une compatibilité et une fiabilité élevées.
    - Facile à utiliser et convivial pour les utilisateurs moyens.
    - Peut également créer des supports amorçables et offre des options de mise à niveau et de création d'installations propres.
- **Cas d'utilisation :**
    - Pratique pour créer des médias d'installation amorçables et effectuer des mises à niveau ou des installations propres de Windows.

En résumé, Rufus est plus puissant et flexible en termes d'options de personnalisation, ce qui peut être utile si vous avez des besoins spécifiques en matière de médias d'installation. Les outils de création de supports Windows sont plus simples à utiliser et sont une option solide pour la plupart des utilisateurs qui souhaitent installer ou mettre à niveau Windows. Le choix entre les deux dépendra de vos préférences et de vos besoins spécifiques.

### installer Windows 10 sur une tour équipée d'une carte mère X79 et d'un processeur Intel Core i7, voici les étapes générales à suivre :

1. **Téléchargement de l'image ISO de Windows 10 :** Rendez-vous sur le site Web de Microsoft et téléchargez l'image ISO de Windows 10.
2. **Création d'un support d'installation :** Utilisez Rufus pour créer une clé USB amorçable à partir de l'image ISO de Windows 10. Choisissez "Image disque" comme option dans Rufus.
3. **Configurer le BIOS/UEFI :** Démarrez votre ordinateur et accédez au BIOS/UEFI en appuyant généralement sur la touche "Suppr" ou "F2" au démarrage. Assurez-vous que l'option de démarrage UEFI est activée si votre système prend en charge l'UEFI.
4. **Démarrer à partir de la clé USB :** Insérez la clé USB que vous avez créée et redémarrez l'ordinateur. Sélectionnez la clé USB comme périphérique de démarrage dans le menu de démarrage.
5. **Installer Windows 10 :** Suivez les étapes de l'assistant d'installation de Windows 10. Vous devrez sélectionner le disque dur ou SSD où vous souhaitez installer Windows, configurer les paramètres régionaux et créer un compte utilisateur.
6. **Activer Windows :** Une fois l'installation terminée, vous devrez peut-être activer Windows 10 en utilisant une clé de produit valide.
7. **Mettre à jour les pilotes :** Après l'installation, il est recommandé de mettre à jour les pilotes de votre matériel, y compris les pilotes de la carte mère, de la carte graphique, etc.
8. **Configurer les paramètres :** Personnalisez les paramètres de Windows 10 selon vos préférences, installez des programmes et configurez vos applications.

Ces étapes vous guideront tout au long du processus d'installation de Windows 10 sur votre tour équipée d'une carte mère X79 et d'un processeur Intel Core i7. Assurez-vous de sauvegarder vos données importantes avant de commencer l'installation.

### Le "Générateur de support de secours" et "Acronis Universal Restore" sont deux fonctionnalités distinctes dans Acronis True Image. Voici leurs différences :

1. **Générateur de support de secours :**
Le Générateur de support de secours vous permet de créer un support de démarrage autonome (clé USB, CD/DVD, etc.) qui contient une version de secours d'Acronis True Image. Ce support de secours vous permet de restaurer vos sauvegardes et de récupérer votre système en cas de panne majeure ou de dysfonctionnement du système d'exploitation.
2. **Acronis Universal Restore :**
Acronis Universal Restore est une fonctionnalité spécifique d'Acronis True Image qui vous permet de restaurer une image système sur un matériel différent (ordinateur avec une configuration matérielle différente). Cela peut être extrêmement utile lors de la migration vers un nouveau matériel, car cela permet à l'image de fonctionner sur la nouvelle configuration matérielle en ajustant les pilotes et les paramètres.

En résumé, le Générateur de support de secours est utilisé pour créer un support de démarrage autonome pour l'utilisation générale d'Acronis True Image, tandis qu'Acronis Universal Restore est une fonctionnalité spécifique qui vous permet de restaurer une image système sur un matériel différent en ajustant automatiquement les paramètres et les pilotes.

<!> Le générateur de support est à faire pour chaque ordi (une clé par ordi) car la fonction avancée qui permet qu’un backup d’un ordi aille sur un autre est un peu compliquée 

### Dans Acronis Media Builder, le choix entre "Simple" (ou "Normal") et "Avancé" dépend de vos besoins et de votre niveau de personnalisation. Voici ce que chaque option signifie :

1. **Simple (ou Normal) :** Cette option est conçue pour les utilisateurs qui veulent créer rapidement un support de secours sans trop de personnalisation. Acronis Media Builder créera un support de démarrage avec les paramètres par défaut, y compris les pilotes génériques pour la plupart du matériel. C'est une option pratique si vous voulez simplement avoir un support de secours en cas de besoin.
2. **Avancé :** L'option avancée vous permet de personnaliser davantage le processus de création du support de secours. Vous pouvez spécifier les pilotes spécifiques nécessaires pour le matériel de votre ordinateur, ajuster les options de création du support et personnaliser certains paramètres. C'est utile si vous avez un matériel spécifique qui nécessite des pilotes particuliers pour fonctionner correctement avec Acronis.

Si vous êtes à l'aise avec la personnalisation et que vous savez quels pilotes sont nécessaires pour votre matériel, l'option "Avancé" vous offre plus de contrôle sur la création du support de secours. Si vous voulez simplement créer rapidement un support de secours avec les paramètres par défaut, l'option "Simple" ou "Normal" est suffisante.

### MAC OSX backups système, des backups de fichiers incrémentaux et planifier des routines de backup de fichiers incrémentaux avec Carbon Copy Cloner :

### Backup système :

1. Ouvrir Carbon Copy Cloner.
2. Sélectionner votre disque de démarrage comme source.
3. Sélectionner le disque de destination pour le backup.
4. Cocher "Backup tout le contenu du volume source" pour copier tous les fichiers et dossiers du disque source.
5. Cliquer sur "Cloner maintenant" pour démarrer le backup.
6. Le backup système sera créé sur le disque de destination.

### Backup de fichiers incrémental :

1. Ouvrir Carbon Copy Cloner.
2. Sélectionner les fichiers et dossiers que vous souhaitez sauvegarder.
3. Sélectionner le disque de destination pour le backup.
4. Cliquer sur "Configurer le backup".
5. Cocher "Backup incrémental" pour ne sauvegarder que les fichiers modifiés ou ajoutés depuis le dernier backup.
6. Choisir la fréquence à laquelle vous souhaitez que le backup soit effectué (par exemple, quotidien, hebdomadaire, mensuel).
7. Cliquer sur "Configurer" pour enregistrer les paramètres de backup.
8. Cliquer sur "Lancer le backup" pour commencer le backup de fichiers.

### Planification de routines de backup de fichiers incrémentaux :

1. Ouvrir Carbon Copy Cloner.
2. Sélectionner les fichiers et dossiers que vous souhaitez sauvegarder.
3. Sélectionner le disque de destination pour le backup.
4. Cliquer sur "Configurer le backup".
5. Cocher "Backup incrémental" pour ne sauvegarder que les fichiers modifiés ou ajoutés depuis le dernier backup.
6. Choisir la fréquence à laquelle vous souhaitez que le backup soit effectué (par exemple, quotidien, hebdomadaire, mensuel).
7. Cliquer sur "Planifier" pour configurer les paramètres de planification.
8. Choisir l'heure et la fréquence à laquelle vous souhaitez que le backup soit effectué.
9. Cliquer sur "Configurer" pour enregistrer les paramètres de backup et de planification.
10. Cliquer sur "Lancer le backup" pour commencer le backup de fichiers.

J'espère que ces instructions vous aideront à effectuer des backups système, des backups de fichiers incrémentaux et à planifier des routines de backup incrémentales de fichiers avec Carbon Copy Cloner.

## Utilisation des adresses IP fixes et des masques de sous-réseau pour configurer 6 ordinateurs sur Windows 10 et Mac OSX avec le QNAP TS-453BT3

Pour configurer 6 ordinateurs sur Windows 10 et Mac OSX avec le QNAP TS-453BT3, il est important de configurer des adresses IP fixes et des masques de sous-réseau pour éviter tout chevauchement d'adresses IP. Voici les étapes à suivre :

### Étape 1 : Planifier votre réseau

Avant de commencer à configurer les adresses IP et les masques de sous-réseau, planifiez votre réseau. Pensez à la façon dont vos appareils seront connectés et à la hiérarchie de votre réseau. Cela vous aidera à déterminer les plages d'adresses IP et les masques de sous-réseau que vous devez utiliser.

### Étape 2 : Utiliser des plages d'adresses IP privées

Utilisez des plages d'adresses IP privées pour votre réseau local, comme 192.168.x.x ou 10.x.x.x. Évitez d'utiliser des adresses IP publiques, car elles sont réservées pour une utilisation sur Internet.

### Étape 3 : Utiliser des masques de sous-réseau appropriés

Utilisez des masques de sous-réseau appropriés pour votre réseau. Un masque de sous-réseau détermine le nombre d'adresses IP disponibles dans une plage d'adresses IP. Plus le masque est petit, plus il y aura d'adresses IP disponibles.

### Étape 4 : Assigner des adresses IP fixes

Assignez des adresses IP fixes à tous les périphériques de votre réseau, y compris les ordinateurs, les imprimantes et les routeurs. Cela vous permettra de configurer plus facilement des règles de pare-feu et de routage.

### Étape 5 : Utiliser des adresses IP réservées

Utilisez des adresses IP réservées pour les périphériques qui ont besoin d'une adresse IP fixe. Les adresses IP réservées sont des adresses IP qui sont assignées à des périphériques spécifiques et qui ne seront pas assignées à d'autres périphériques.

### Étape 6 : Configurer les adresses IP et les masques de sous-réseau

Pour configurer les adresses IP et les masques de sous-réseau sur Windows 10 et Mac OSX, suivez les étapes indiquées dans les sections précédentes. Assurez-vous que chaque ordinateur a une adresse IP unique et que les plages d'adresses IP ne se chevauchent pas.

### Étape 7 : Configurer les connexions réseau

Connectez les ordinateurs au QNAP TS-453BT3 à l'aide des connexions Ethernet, Ethernet 10GB ou Thunderbolt 3. Assurez-vous que chaque connexion est correctement configurée avec une adresse IP et un masque de sous-réseau appropriés.

En suivant ces étapes, vous devriez être en mesure de configurer 6 ordinateurs sur Windows 10 et Mac OSX avec le QNAP TS-453BT3 sans chevauchement d'adresses IP. Si vous rencontrez des problèmes, n'hésitez pas à contacter un professionnel de l'informatique pour obtenir de l'aide.