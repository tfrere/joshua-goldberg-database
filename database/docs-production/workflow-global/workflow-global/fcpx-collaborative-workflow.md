# FCPX Collaborative Workflow

Le flux de travail collaboratif dans Final Cut Pro X (FCPX) est conçu pour permettre à plusieurs monteurs de travailler sur un projet simultanément, tout en minimisant les conflits et les problèmes de synchronisation. Si vous avez déjà un serveur de stockage en réseau (NAS), c'est une excellente première étape. Voici quelques éléments clés à prendre en compte :

### Préparation

1. **Centralisez les médias** : Assurez-vous que tous les fichiers média sont stockés sur le NAS et sont accessibles à toutes les stations de travail.
2. **Gestion des fichiers** : Créez une structure de dossiers claire et compréhensible sur le NAS pour faciliter le partage des ressources.
3. **Librairies FCPX** : Vous pouvez choisir de créer une librairie par projet ou une grande librairie qui contient plusieurs projets.

### Collaboration

1. **Librairie Maître et Librairies Locales** :
    - **Librairie Maître** : Une librairie maître peut être créée sur le NAS, qui contient tous les médias et peut être accessible en lecture-seule par les monteurs.
    - **Librairies Locales** : Chaque monteur peut avoir une librairie locale sur son propre système où il/elle peut créer des projets et des séquences.
2. **Événements et Projets** :
    - Créez des événements pour diviser le travail. Par exemple, un événement pour les interviews, un autre pour les séquences B-roll, etc.
    - Chaque monteur peut travailler sur des projets spécifiques au sein de ces événements.
3. **XML de FCPX** : Utilisez des fichiers XML pour échanger des séquences et des projets entre librairies. Vous pouvez exporter un projet ou un événement en tant que fichier XML depuis une librairie locale et l'importer dans la librairie maître.
4. **Conflits** : Pour éviter les conflits, assurez-vous que deux monteurs ne travaillent pas sur le même projet ou la même séquence simultanément. Une communication claire est cruciale ici.

### Sauvegarde et Synchronisation

1. **Copie de sécurité** : Assurez-vous d'avoir une stratégie de sauvegarde en place pour le NAS.
2. **Synchronisation** : Le NAS devrait être capable de se synchroniser rapidement afin que les modifications soient visibles par tous les monteurs le plus rapidement possible.

### Logiciels Tiers

Il existe également des solutions tierces pour la collaboration FCPX comme PostLab, qui aide à la gestion de version et à la collaboration à distance.

Notez que la collaboration en temps réel n'est généralement pas possible avec FCPX en utilisant seulement des librairies et des fichiers partagés, contrairement à certains autres systèmes de montage qui offrent des fonctionnalités de collaboration en temps réel.

### Exporter de la Librairie Locale

1. **Sélectionnez le Projet ou la Séquence** : Dans votre librairie locale, sélectionnez le projet ou la séquence que vous avez terminé.
2. **Exporter en XML** : Allez dans `Fichier` > `Exporter` > `XML...`. Sauvegardez le fichier XML sur un emplacement temporaire ou directement sur le NAS si cela est possible.

### Importer dans la Librairie Maître

1. **Accédez à la Librairie Maître** : Ouvrez la librairie maître qui est stockée sur le NAS.
2. **Importer XML** : Allez dans `Fichier` > `Importer` > `XML...`. Sélectionnez le fichier XML que vous avez exporté depuis votre librairie locale.
3. **Vérification** : Après l'importation, vérifiez que toutes les références aux médias sont correctes et que la séquence apparaît comme prévu.

### Synchronisation des Médias

Si vous avez ajouté de nouveaux médias dans votre librairie locale qui ne sont pas déjà dans la librairie maître, vous devrez également vous assurer de les transférer. Cela peut généralement être fait en copiant les fichiers médias pertinents dans le dossier correspondant sur le NAS.

### Communication

Étant donné que vous travaillez en équipe, assurez-vous de communiquer clairement lorsque vous avez terminé ces étapes pour éviter tout conflit ou toute confusion.

En suivant ces étapes, vous devriez être en mesure de transférer efficacement des projets ou des séquences individuelles de votre librairie locale à la librairie maître sur le NAS.

### Créer une Librairie Locale à partir de la Librairie Maître

1. **Dupliquez la Librairie Maître** : Vous pouvez le faire en faisant un clic droit sur la librairie maître dans FCPX et en choisissant "Dupliquer". Cela vous donnera une copie exacte de la librairie maître.
2. **Transférez la Librairie Dupliquée Localement** : Si vous n'avez pas déjà dupliqué la librairie directement sur votre système, déplacez la librairie dupliquée sur votre système local.
3. **Réduisez la Librairie** : Si la librairie maître est volumineuse, vous voudriez peut-être retirer les éléments non essentiels. Par exemple, vous pouvez supprimer des événements ou des projets qui ne sont pas pertinents pour vous.

### Gestion des Médias

- **Media Originaux** : Normalement, les médias d'origine resteront sur le NAS. Vous ne voudriez pas les dupliquer localement car ils peuvent prendre beaucoup d'espace.
- **Media Proxy ou Optimisé** : Vous pouvez travailler avec des médias proxy ou optimisés qui sont beaucoup plus petits et gérables. Si vous savez que vous travaillerez hors ligne, assurez-vous que ces fichiers sont stockés localement.

Pour s'assurer que vous travaillez en mode proxy :

1. Allez à `Final Cut Pro` > `Préférences` > `Lecture` et cochez l'option `Utiliser les médias proxy` si elle n'est pas déjà cochée.
2. Assurez-vous d'avoir des médias proxy pour tous vos clips. Si ce n'est pas le cas, vous pouvez les créer en sélectionnant les clips dans votre navigateur, en faisant un clic droit, et en choisissant `Transcoder les médias...`.

### Accès au NAS

- Si vous travaillez avec des médias proxy localement, vous n'avez pas besoin d'être constamment connecté au NAS.
- Cependant, si vous avez besoin de basculer vers les médias originaux ou d'exporter avec une qualité maximale, vous devrez être connecté au NAS.

### Remarque Importante

Lorsque vous êtes prêt à fusionner votre travail avec la librairie maître, vous utiliserez l'exportation et l'importation XML comme mentionné précédemment. Il est essentiel de veiller à ne pas écraser le travail d'autres monteurs.

La clé est une bonne organisation et une communication claire avec les autres monteurs pour garantir que tout le monde est sur la même longueur d'onde et que les conflits sont minimisés.

Some articles : 

[https://www.macprovideo.com/article/final-cut/collaborative-video-editing-using-final-cut-pro-x](https://www.macprovideo.com/article/final-cut/collaborative-video-editing-using-final-cut-pro-x)

[https://workflow.frame.io/guide/collaborative-editing-fcpx](https://workflow.frame.io/guide/collaborative-editing-fcpx)