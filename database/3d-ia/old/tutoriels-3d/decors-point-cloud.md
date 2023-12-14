# Décors point cloud

<aside>
💡 Une fois la modélisation de base terminée sur Blender 3.5.1, il est utile de low-polyser et de remesh l’objet pour avoir un asset facile à travailler

</aside>

1. Je commence par baker tous les matériaux de mon objet en un seul png unique. Pour ce faire je l’unwrap et je le bake en combine ou en diffuse. Ne pas oublier de placer un slot avec une image crée “bake” en 2k ou hd vide, unplugged, que je laisse sélectionné. Je bake dans “active image texture”. Ne pas oublier également de pack l’image (image view > files > pack)
2. Assigner les couleurs aux vertices. Dans object data > color attributes je créé un nouvel attribut. 
3. Dans le menu render, je vais dans l’onglet bake, je sélectionne combine et je décoche direct et indirect light pour ne garder que la couleur. Dans l’output je sélectionne “Active attribute”.
4. Je peux exporter l’objet en fbx avec les paramètres suivants :

![to cc.PNG](De%CC%81cors%20point%20cloud%2079b8b079e5644667960644240a7a3c32/to_cc.png)

1. J’ouvre CloudCompare v2.14.4. File > import > le .fbx
2. Je clique sur le .fbx importé (qui, si l’export/import est correctement réalisé, s’affiche avec ses textures) et je clique sur le project points dans la barre d’outil.

![cc.PNG](De%CC%81cors%20point%20cloud%2079b8b079e5644667960644240a7a3c32/cc.png)

1. Je set le nombre de points (10000000 pour le capitol par ex, donc entre 1 et 10 millions)
2. Je save le fichier en sélectionnant le point cloud nouvellement créé (automatiquement en .las).

<aside>
💡 Import dans Unreal 5.2

</aside>

1. Je télécharge depuis l’Epicstore le plugin LiDAR import.
2. Je l’active depuis edit > plugin 
3. Dans le content browser, j’import le fichier .las
4. Je drag and drop dans la scène : Le point cloud est normalement désormais totalement affiché.
5. Attention, il est nécessaire (sauf mise à jour) de réimporter les lidar à chaque ouverture d’unreal…
6. Simplement faire un shader avec un vertex en base color pour avoir control sur le rendu du point.