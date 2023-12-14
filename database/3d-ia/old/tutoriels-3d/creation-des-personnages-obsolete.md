# Création des personnages (obsolète)

<aside>
<img src="https://www.notion.so/icons/child_gray.svg" alt="https://www.notion.so/icons/child_gray.svg" width="40px" /> La première étape est la génération d’un personnage. Pour cela j’utilise Blender 3.5.1 et MB-Lab 1.7.8.

</aside>

1. Dans Blender 3.5.1, je créé un nouveau fichier que j’enregistre.
2. Dans l’onglet render, je passe sur le moteur de rendu ******Cycles****** et je passe de rendu CPU à GPU compute. (Si non activé par défaut, ****************************************************edit > preferences > system >acceleration structure> CUDA pour Nvidia ou autre)****************************************************

    
    ![2.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/2.png)
    
3. Pour plus de confort, set up les world settings en white background à 0.75 de strenght (ambiant light)

    
    ![3.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/3.png)
    
4. je commence par installer et activer l’addon MB-Lab.

[MB-Lab-master.zip](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/MB-Lab-master.zip)

1. *Edit>preferences>Add-on>Install>*sélectionner le fichier zip et *approuver>cocher* la check-box à coté du nom de l’addon. Il apparaît maintenant dans le menu déroulant tout à droite de la fenêtre 3d Viewport en object mode.

![Capture.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/Capture.png)

1. Il suffit ensuite de choisir le human type dans “select” et de lancer “Create character”. à noter qu’il est possible de réaliser des métissage plus tard dans le process.
2. Une fois les réglages de “mass” et de “age” obtenus, il est essentiel d’aller dans l’onglet “Finalize tool” et de cliquer sur “finalize character”, une fenêtre d’enregistrement s’ouvre et permet d’enregistrer toutes les maps du personnage dans des fichiers images externes. 
3. Pour s’assurer que tous les fichiers ne sont pas juste liés au .blend, il suffit d’aller dans ***************************************file > External Data > Pack ressources.*************************************** 

MANQUE LA PARTIE CLO3D

<aside>
<img src="https://www.notion.so/icons/cursor-click_gray.svg" alt="https://www.notion.so/icons/cursor-click_gray.svg" width="40px" /> L’avatar est maintenant près à passer dans mixamo. Sinon, il est aussi possible de l’annimer directement dans blender avec le rig fourni par MbLab.

</aside>

**Avec Mixamo**

1. J’export le modèle entier en le sélectionnant en object mode*>file>export>wavefront(.obj)* avec les paramètres suivants : 
    
    ![test hum_blush.png](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/test_hum_blush.png)
    
2. Je compresse les deux fichiers obtenus (.obj pour le mesh et .mtl pour les textures, en un seul fichier .zip avec winrar).
3. Je vais sur [mixamo.com](http://mixamo.com) >upload character > drag and drop le .zip obtenu directement dedans
4. Après le rigging et le choix de l’animation, je clique sur download, et dans le menu, je laisse le fichier sur .fbx binaire  et je sélectionne 24fps en frame rate.
5. De retour dans Blender, je vais dans File>import>fbx et dans la fenêtre je change le Scale à “100” (Mixamo export des .fbx avec pour unité le mètre, et Blender le centimètre)

*L’avatar animé et texturé, sans cheveux ni poils devrait apparaître.*

1. Il suffit alors de mettre la coupe finale en selectionnant les vertex (soit weight paint soit directement en edit mode) >stocker dans un vertex group > ParticleSystem > Hair > Pour l’instant je suggère 1000 particles et entre 20 et 40 interpolated children suivant le rendu > ne pas oublier de plug le vertex group dans la case “density” du particle system pour les générer aux endroits voulus. 
Pour les réglages de taille (>particle System> Hair shape), je suggère pour l’instant une diameter root de 0.5 et un diameter scale de 0.001.

<aside>
<img src="https://www.notion.so/icons/arrow-right_gray.svg" alt="https://www.notion.so/icons/arrow-right_gray.svg" width="40px" /> L’avatar est maintenant terminé et près à être envoyé dans Unreal 5.2.0.

</aside>

1. Avant de commencer les exports, il est encore une fois nécessaire de nettoyer les fichiers liées et hébergés par le .blend. Comme tout à l’heure *File > Clean-Up > Unused Data blocks* et *File > Clean-Up > Recursive Unused Data blocks.*
2. Ensuite il est utile de s’assurer que les fichiers images sont bien hébergés dans le .blend. Là encore ***************************************file > External Data > Pack ressources.*************************************** 
3. à défaut d’avoir l’addon blender to unreal (non dispo dans 5.2 pour l’instant), la solution réside dans un double export. Un qui prendra en charge le squelette, et l’autre l’animation. 
J’export donc, en prenant soin de sélectionner à la fois le rig et le mesh avec ces deux paramètres : 

Le premier, appelé RIG : 

![4.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/4.png)

Le deuxième, ANIM, le même avec le bake animation actif et sans le NLA : 

![6.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/6.png)

1. Ensuite, dans unreal, j’import le premier (RIG) avec les paramètres suivant : 

![7.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/7.png)

1. J’import le deuxième, cette fois ci en décochant la case “Skeletal mesh” et en cochant la case “import animations”. Comme ci-dessous, j’inclu dans la case skeletton le fichier d’avant.

![8.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/8.png)

1. Je drag and drop le fichier ANIM dans la scène, il est possible qu’il soit down scale x10 ou x100 (à régler).
2. Il suffit d’aller dans le menu déroulant à droite avec l’objet sélectionné, animation mode > animation asset puis dans le menu déroulant, sélectionner l’animation juste importée (encore une fois, il est possible que l’objet se downscale, je n’ai pas encore d’autre solutioon que le up scale directement sur unreal).

<aside>
<img src="https://www.notion.so/icons/child_red.svg" alt="https://www.notion.so/icons/child_red.svg" width="40px" /> L’avatar est maintenant importé, animé et texturé dans Unreal, il ne manque plus qu’a importer le wireframe ainsi que les cheveux et barbe.

</aside>

1. Pour les cheveux, je commence par dupliquer l’avatar dans Blender, et a cacher l’armature dans le viewport et les render.
2. Ensuite, dans les *Particules settings > Render* je décoche “Show Emitter”.
3. De même dans *Particules settings > Viewport Display*.
4. *Files > export > Alembic .abc* avec les paramètres suivant et les cheveux sélectionnés.
 

![11.PNG](Cre%CC%81ation%20des%20personnages%20(obsole%CC%80te)%20246815349efd4d709d0ebfd3d6f5b17e/11.png)

1. Je ferme blender et j’ouvre le projet Unreal. *Edit > Plug-in >* j’active Groom alembic et Groom.
2. Je transforme l’avatr importé précédemment en blueprint (dans *l’outliner > clique sur l’avatar > nodes logo à coté de add > Première case de sélection dans la nouvelle fenêtre*).
3. J’ouvre le Blueprint editor en faisant un clic droit sur l’objet .
4. Dans la fenêtre Components en haut à gauche, j’add un *groom object.*
5. Dans la fenêtre detail à droite, je drag and drop le .abc dans groom asset depuis le content folder.