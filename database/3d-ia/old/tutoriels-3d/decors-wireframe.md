# Décors Wireframe

<aside>
💡 Pour créer un faux wireframe, j’utilise les Geometry nodes de Blender et la fonction mesh to curve to mesh, en jouant sur un bug pour le mapping des textures. Le workflow est assez complexe et comprend plusieurs troubleshooting possibles.

</aside>

1. Je modélise un objet, ou je récupère un asset. 
2. Je le duplique pour éviter toute action destructrice 
3. La première chose est de s’assurer d’avoir un objet facile à travailler. Pour cela : 
4. Si l’objet à un parent (ou est lié à un empty), je l’unlink.
5. Si l’objet est divisé en plusieurs parties, Je les fusionne (cmd+J).

<aside>
💡 Vérifier si : 
-Tous les objets ont une seule uv map qui porte le même nom à chaque fois.
-Tous les objets n’ont pas de modifiers qui n’ont pas été appliquer (sinon, les appliquer) 
-Tous les objets n’ont pas de vertex group ou de weight group du même nom (si inutile, les supprimer)

</aside>

1. J’ai maintenant un seul objet. je doit maintenant fusionner tous les matériaux pour avoir une seule diffuse map. 
2. Pour ce faire, j’unwrap l’objet nouvellement créé sur une nouvelle UV map (sinon le mapping des matériaux existants seront faussés).
3. J’ajoute un image texture node branché à un UVmap node, dans lequel est séléctionné mon dernier unwrap, dans lequel je créé une nouvel image 4k “Nomdel’objet_4K_Diffuse”.
4. Si j’ai plusieurs matériaux, j’ajoute ce “double” nœud à chacun des matériaux, en prenant soin de laisser sélectionné l’image texture à chaque fois.
5. Je bake le diffuse de l’objet dans le render menu en, sélectionnant active “image texture” dans la target, et en ne garder coché que “color”.

<aside>
💡 Si le cas apparaît d’un objet dont on doit conserver les détails en normal ou bump map, il faudra (et je le redoute) probablement utiliser un displacement modifier avec la normal map inversée et passé en noir et blanc dans photoshop… à éviter en tous cas.

</aside>

1. J’ai maintenant un seul objet dont la diffuse map est baké, il peut être judicieux de le dupliquer encore une fois.
2. Je vais pouvoir ajouter un Géometry node modifier et l’ouvrir dans le geometry nodes editor. Je créé le node suivant : 

![capture wire.PNG](De%CC%81cors%20Wireframe%201a555bd26cee47e3ac45a538e941b232/capture_wire.png)

1. L’idée est simple : Chaque arrête est convertie en tube via le mesh to curve > curve to mesh et le Curve circle (résolution > 2 et radius très faible (plus facile à gérer avec un Math node sur Divide).
2. La partie compliquée de ce pipe réside dans le mapping des couleurs. Pour le réaliser : 
-J’ajoute un “store named attribute” node, branché en  “Color” et “Face Corner” (même data que les UV map). Je nome l’attribut que je vais utiliser (ex : col).
-J’ajoute une Image texture dans laquelle j’ajoute ma diffuse map.
-Je branche cette image comme valeur de couleur, et dans l’output de mon groupe input.
-Il est ensuite nécessaire d’aller dans les réglages des modifiers et je clique sur le l’icon de normal, pour ensuite sélectionner mon UV map d’origine. 

![Capturewire4.jpg](De%CC%81cors%20Wireframe%201a555bd26cee47e3ac45a538e941b232/Capturewire4.jpg)

1. J’ajoute un nouveau material que je branche à la fin de mon geometry node avec un ‘set material’
2. Je branche un “color attribute” à la base color de ce material en selectionnant l’attribut que j’ai créé à l’étape 14. 

![Capturewire.PNG](De%CC%81cors%20Wireframe%201a555bd26cee47e3ac45a538e941b232/Capturewire.png)

1. Les couleurs doivent s’afficher.

<aside>
💡 à ce niveau, il sera peut-être nécessaire d’ajuster le meshage pour obtenir un résultat convaincant.

</aside>

1. Pour ce faire, j’utilise un pipe tel que le suivant : 

![capture wire2.PNG](De%CC%81cors%20Wireframe%201a555bd26cee47e3ac45a538e941b232/capture_wire2.png)

1. Si la trame est au contraire trop faible, il suffit de placer un node subdivision juste après le store named attribute !

<aside>
💡 Pour exporter dans Unreal, il est nécessaire d’attribuer cet attribut comme vertex color de l’objet, puisqu’il n’a pas réellement d’UV map.

</aside>

1. Pour ce faire, il suffit d’appliquer le modifier (bien penser à dupliquer l’objet avant, il sera sûrement nécessaire d’ajuster le radius des tubes). 
2. Une fois appliqué, le color attribute devrait apparaître dans les vertex color (voit dans le menu object data). 
3. Je peux donc exporter mon object en fbx avec les mêmes paramètres que pour les point cloud.

![fbx.PNG](De%CC%81cors%20Wireframe%201a555bd26cee47e3ac45a538e941b232/fbx.png)

1. Dans Unreal, simplement ajouter un matériau avec un vertex color branché dans la base color.