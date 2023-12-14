# Workflow 3D/Stable diffusion

# Tests

Tests de 2 méthodes différentes pour “diffuser” une vidéo, c’est à dire pour remplacer le sujet principal tout en conservant ses mouvements et si possible son expression. Pour les vidéos prises en plan rapproché du visage, l’input est toujours le même, une vidéo d’une quarantaine de secondes prise au téléphone:

### Img2Img only:

Ici, on utilise simplement une séquence d’images en tant qu’input, et on applique une diffusion img2img sur chacune d’entre elles individuellement, avec le même prompt:

[Seq3Upscaled.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Seq3Upscaled.mp4)

J’ai aussi fait une version plus “anime” qui est aussi très chaotique:

[Seq2.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Seq2.mp4)

Le résultat est très instable, mais à mon avis très intéressant. On pourrait assez facilement jouer sur la stabilité en retirant des images pour altérer la cadence, puis en passant par Flowframes pour retrouver la cadence initiale, mais avec un optical flow qui transitionnerait de manière plus fluide entre les images. Comme ça:

[Seq3Upscaled_halved-2x-RIFE-RIFE4.0-30fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Seq3Upscaled_halved-2x-RIFE-RIFE4.0-30fps.mp4)

En retirant la moitié des images, réduisant la fréquence d’images de 30 à 15, puis en repassant à 30 par Flowframes, on peut légèrement lisser le mouvement frénétique. On pourrait répéter ce processus plusieurs fois, mais cela donne un effet de morphing assez dur entre les images, et le mouvement devient répétitif.

Ici, le paramètre de denoising_strength était élevé, ce qui fait que l’image de base a été radicalement réinterprétée, et on n’en garde que la forme. En jouant avec les paramètres et les prompts, on pourrait certainement avoir un résultat qui conserve mieux les mouvements du visage lorsque le personnage parle.

### 1 keyframe en img2img + Ebsynth :

Ici, on utilise l’input de base, la vidéo normale, avec Ebsynth, en lui donnant une seule keyframe, située plutôt vers le début.

[Seq3_Ebsynth.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Seq3_Ebsynth.mp4)

Le résultat se dégrade progressivement à partir de la keyframe sélectionnée. Pour maintenir le résultat à un degré de stabilité cohérent, on peut utiliser plusieurs keyframes:

### 17 keyframes en img2img + Ebsynth

[Ebsynth_17Keys.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Ebsynth_17Keys.mp4)

Ici, on utilise 17 keyframes, et on interpole entre elles avec des crossfades simples. On pourrait utiliser autre chose que des crossfades, qui sont très visibles dans cette configuration, mais cette manière de faire empêche en tout cas la dégradation totale de la vidéo, et la fait ressembler plus à l’input en termes de mouvement, avec une cohérence picturale plus stable.

# Temporal consistency avec ControlNets:

Deuxième méthode. Ici, à partir d’une vidéo input, on sélectionne *n* keyframes, puis les dispose sur une seule image, en grille, à une résolution totale gérable par stable diffusion ( < 1920px). Ensuite, on utilise ControlNet (Ou plutôt un setup Multi-Controlnet avec Lineart, Depth et OpenPose), pour obtenir une diffusion très précise du personnage sur cette image.

### 6keyframes:

![sample-00009resize.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/sample-00009resize.png)

On sépare les keyframes, et on les utilise comme instructions pour ebsynth. Ebsynth génère des images des deux côtés de chaque keyframes, jusqu’à arriver à la keyframe précédente/suivante, ou le début/fin de la séquence d’images. Cela permet de faire transitionner les outputs des différentes générations en mode “escalier”, en utilisant des crossfades entre les séquences qui se superposent:

### + ebsynth :

[talking_6keys.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/talking_6keys.mp4)

Avec cette méthode, il y a d’autres problèmes:

- La stabilité de l’image est inversement proportionnelle à la quantité de mouvement et au degré de changement de position du personnage, par exemple si le personnage se tourne trop rapidement, cela crée des artéfacts dans les zones découvertes.
- Cette méthode fonctionne beaucoup mieux pour des séquences relativement courtes, d’une dizaine de secondes, parce que plus la vidéo est longue, plus les keyframes sont espacées, et plus il ya de chances pour qu’Ebsynth perde le track entre deux keyframes.
- De plus, le nombre maximal de keyframes est difficile à augmenter. On pourrait peut-être aller jusqu’à 9 keyframes, mais il faudrait déjà diminuer la résolution des images, ce qui n’est pas si grave en soi vu la puissance des upscalers, mais qui crée quand même des instabilités dans l’image puisque stable diffusion est entrainé avec des images de 512x512px. Plus on augmente la résolution, plus le risque d’artéfacts et de duplications de parties de l’image augmente.
- On ne peut pas utiliser SDXL, qui est incompatible avec les Controlnets. De plus, SDXL est très récent, et peu de modèles customisés ont été fabriqués pour pouvoir avoir une maitrise de la nature de l’image (Ici, j’ai utilisé CineDiffusion, qui est entrainé sur des images de films et donne une texture plus cinématique à l’image que le modèle SD de base.)

Je pense qu’en choisissant mieux les keyframes, et avec des vidéos un peu moins longues, la cohérence sera encore plus stable.

### ebsynth 24keyframes sur 4 grilles:

Ici, on utilise 4 grilles de keyframes afin de rendre le mouvement plus fluide et de réduire les artéfacts. Ces grilles de keyframes sont diffusées par des controlnets à partir d’inputs d’une vidéo filmée en face cam.

![spritesheet1.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet1.png)

![spritesheet2.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet2.png)

![spritesheet3.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet3.png)

![spritesheet4.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet4.png)

Bien que les images aient été générées à partir d’inputs issus de la même séquence, avec la même balance des blancs, le même éclairage, etc, et qu’ils utilisent tous les mêmes paramètres de diffusion, on remarque que les images sont relativement différentes, notamment au niveau des couleurs. Même l’aspect du personnage varie légèrement entre les différentes grilles. En mouvement, dans la séquence animée, on voit que le personnage change d’aspect toutes les 10 secondes à cause de ces irrégularités entre les grilles:

[24keysTemporalConsistency4K.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/24keysTemporalConsistency4K.mp4)

## Intégration dans un environnement 3D

En admettant que l’on utilise cette séquence pour la pousser dans un registre plus immersif, on peut l’intégrer dans un environnement 3D ou elle réagirait de manière réaliste aux lumières et dans lequel on peut aussi choisir avec plus de précision la position de la caméra. Pour ce faire, il est possible de passer cette séquence d’images par deux filtres:

- Le premier génère pour chaque frame une depthmap, qui détermine la profondeur et la proximité du sujet à la caméra
    
    ![depth_zoe-0000.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/depth_zoe-0000.png)
    
- Le deuxième crée un masque d’opacité qui délimite les contours du sujet, permettant de l’isoler du fond.
    
    ![24keys_TemporalConsistency_Alphamask_00000.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/24keys_TemporalConsistency_Alphamask_00000.png)
    
- Dans Blender, on peut importer notre séquence d’images de base comme une surface plane:
    
    ![ImageAsPlane.PNG](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ImageAsPlane.png)
    
- On la positionne dans l’espace à l’endroit souhaité pour le personnage selon le plan, puis on peut isoler le fond en utilisant le masque d’opacité:
    
    ![AlphaChannel.PNG](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/AlphaChannel.png)
    
- Puis on utilise la Depthmap pour lui donner une profondeur (approximative):
    
    ![Depthmapped.PNG](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Depthmapped.png)
    
- Et enfin, on peut rééclairer le personnage avec Blender en utilisant un shader diffus qui réagit à la lumière:
    
    ![Lit.PNG](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Lit.png)
    

Et le tout est animé, ce qui nous permet de déplacer la caméra, d’utiliser la profondeur de champ, ou de modifier l’éclairage pendant la séquence 

### résultat final (Lumière test flash rouge attention aux yeux):

[depthmapped_4K_MultiControlnet0001-1235.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/depthmapped_4K_MultiControlnet0001-1235.mp4)

Ici, la caméra vibre et recule lentement, changeant la valeur de plan. La depthmap permet de renforcer l’illusion de présence dans l’espace alors que le personnage se rapproche et s’éloigne de l’objectif. La profondeur de champ accommode la distance au personnage au cours de la séquence, et les lumières qui clignotent éclairent le personnage et projettent son ombre sur le mur derrière. La séquence est rendue en 4K, la texture du personnage a été upscalée en 4K depuis une résolution de 960x540.

## Full body Test 1

En utilisant d’abord le plus de keyframes possible avec une grille de 36 keyframes:

### 36 Keyframes 512x512 (2 keyframe/seconde)

![spritesheet_comparison.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet_comparison.png)

Cette méthode ne fonctionne pas. J’espérais qu’en augmentant le nombre de keyframes la stabilité de l’image serait augmentée, mais en fait, il a fallu réduire la résolution de l’image, ce qui rend chaque cellule trop petite et peu détaillée, ce qui en mouvement donne une énorme différence entre les keyframes:

[AECompEbsynth36keys.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/AECompEbsynth36keys.mp4)

Le mouvement du personnage est plus ou moins cohérent, mais il est entrecoupé de manière très visible. C’est parce que les keyframes ne se ressemblent pas assez. De plus, il y a trop de keyframes, qui sont superposées par crossfades successifs dans After Effects, mais elles durent si peu de temps que le crossfade ne permet pas de lisser le mouvement et donne une impression de jump cut. Enfin, la résolution très basse n’est pas favorable à l’upscaling, et le visage est complètement éclaté. Il faut donc utiliser moins de keyframes à une plus haute résolution:

### 9 Keyframes 1024x1024 (0.5 keyframe/seconde)

![spritesheet_comparison2.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/spritesheet_comparison2.png)

Cette méthode donne un résultat au mouvement beaucoup plus fluide:

[Comp9Keys.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Comp9Keys.mp4)

Le personnage reste plus stable, et son visage est un peu plus défini. En utilisant des upscalers, on peut augmenter le niveau de détail et donner a son visage un aspect encore plus précis, même si les upscalers faciaux ont tendance à remplacer les visages de style anime par des visages photoréalistes, ce qui donne des hybrides intéressants:

![Comp_00001.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Comp_00001.png)

Pour cette image, j’ai utilisé un upscaler qui “restaure” les données faciales, ce qui donne un aspect plus photographique au visage, et qui efface aussi le fond de manière rudimentaire. Ce dispositif est provisoire, il sert surtout à préparer le test qui consiste à placer ce personnage dans un espace pour sentir le résultat:

[anime boy in the garden](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/anime%20boy%20in%20the%20garden%20461b2164bfe142d596493e8475bcd74d.csv)

En gros, il faut compter que pour chaque frame d’animation, il y a un nombre d’étapes qui prennent chacun un certain temps de rendu:

1. Extraction des frames de la vidéo et resizing au format SD : 5m
2. Diffusion des keyframes : 30m
3. synchro Ebsynth : 15m
4. Rendu After Effects : 5m
5. Rendu Depthmap : 30m
6. Upscaling + Alpha mask : 60m
7. Rendu Blender : 30s/frame

Il faut compter, en se donnant une marge, 1min de processing passif par frame de vidéo. Pour une séquence de 600 frames, c’est 10h, dont la majorité est passée à faire le rendu dans Blender, que l’on attend jusqu’au dernier moment pour lancer pour la nuit. Ces temps de rendu sont entrecoupés de périodes de travail manuel et d’ajustement qui peuvent durer entre quelques minutes et quelques heures, selon la complexité du plan ou le nombre d’étapes : 

1. Processing de la vidéo input, sélection des keyframes, création des grilles : 10min
2. Ajustement du prompt et réglages des Controlnets dans SD : 3h (Maximum - Chaque génération d’image à haute résolution par Controlnet peut prendre jusqu’à 20min, mais comme ce sont les keyframes qui sont utilisés pour synchroniser l’ensemble de la vidéo, il faut évidemment prendre le temps d’ajuster ces paramètres correctement, et de faire plusieurs générations, ce qui peut prendre jusqu’à 3h)
3. Extraction des keyframes, synchronisation dans Ebsynth avec la vidéo input, réglages Ebsynth : 15min
4. Réglages de SD pour les exports de la depthmap et du masque alpha : 20min
5. Importation dans Blender, réglages du shader et des modifiers, ajustement des lumières, des caméras, mouvement de caméra, profondeur de champ, compositing : 3h

Ces temps incompressibles sont nécessaires pour chaque plan, ce qui oblige à une logique de travail qui s’organise autour de longs plan-séquences de plus d’1min chacun. On peut ensuite les découper au montage, mais il faut penser chaque plan comme une unité de base.

Chaque plan prendra environ une journée à fabriquer avec cette méthode, ce qui semble très long, mais en utilisant des plans de plus d’une minute, on peut facilement faire plus de 10min d’animation par semaine, ce qui est en fait extrêmement productif, et à un niveau correct en termes de rendu.

La méthode favorise largement les plans plutôt rapprochés, gros plans de visage, et s’améliore plus la ressemblance entre le sujet de la vidéo initiale ressemble au résultat souhaité. Il est donc préférable de porter des vêtements similaires, ou une perruque pour faciliter la tâche à Stable Diffusion. Le résultat est de plus très fluctuant, il dépend énormément du modèle utilisé, et du prompt. Par contre, la qualité de l’input n’est pas un facteur crucial - c’est toujours mieux d’avoir des images HD bien éclairées, mais une prise de vue au téléphone peut fonctionner aussi bien. Plus le personnage est stylisé, par exemple dans le cas d’un design anime, plus il sera instable et réagira de manière inexacte aux mouvements de la vidéo input. Ce problème est dû à Ebsynth, qui colle les pixels de la keyframe sur les pixels de l’input correspondant, alors que la forme d’un personnage stylisé ne correspond pas toujours exactement aux contours de la vidéo input correspondante, ce qui donne des marges entre les deux qui seront emportées par le mouvement (cela donne les flux de couleur qui suivent les mouvements alors qu’ils appartiennent au fond et non à la forme du personnage même).

### Résultat - personnage plein pied, 9 keyframes sur 20 secondes, intégré dans un espace 3D:

[CompBlender_low.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/CompBlender_low.mp4)

Avec 9 Keyframes, Ebsynth, depthmap, alpha mask, séquence de 16 secondes, dans un environnement 3D avec mouvement de caméra, profondeur de champ et éclairage dynamique.

Il y a encore un certain nombre d’artéfacts car il y a peu de de keyframes et au fait que le background ait été retiré avec un algorithme un peu simpliste. En générant plusieurs grilles comme on l’a fait précédemment pour le visage, on pourrait obtenir un résultat moins liquide. Cet effet de liquéfaction est plus prononcé lorsque le personnage bouge beaucoup ou se tourne, comme si il emportait avec lui une partie du décor.

Dans le plan taille (premier plan de la séquence), on observe aussi les effets de la restauration du visage sur le personnage : bien qu’il soit lui même en style anime, le visage a été upscalé par un algorithme photoréaliste, ce qui donne l’aspect hybride mentionné plus haut. En mouvement, comme chaque image est upscalée indépendamment des autres, cela donne une sensation de vibration des traits du visage, par rapport au mouvement du corps, qui est plus homogène.

### Test : Environnement et personnage diffusés, maîtrise du degré d’indétermination de l’image

En fabriquant des images en mouvement à l’aide de l’intelligence artificielle, on observe que leur propriété plastique la plus marquante est ce que l’on pourrait appeler la “cohérence temporelle” de l’image animée, qui dépend d’un très grand nombre de facteurs et varie dans son aspect selon le processus utilisé pour les fabriquer.

Ce que j’entends par “cohérence temporelle”, c’est en fait le rapport de chaque image d’une séquence à celle qui la précède, et à celle qui la suit. Dans une séquence d’images capturées par une caméra lors d’une prise de vue normale, la cohérence temporelle est une variable bien plus stable et tenue pour acquise : chaque nouvelle image consistera en une version de l’image précédente dont certains pixels se seront déplacés si il y a eu un mouvement, que ce soit le mouvement de la caméra ou celui d’un sujet dans le cadre.

Dans une séquence d’images générées artificiellement, ou réinterprétées à partir d’une séquence en prise de vue réelle, ce rapport temporel direct entre les images est brisé: chaque image est désormais considérée et traitée indépendamment des autres.

[Seq2.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Seq2%201.mp4)

Ici, on utilise une vidéo filmée à 30 images par secondes, et qui contient environ un millier d’images. Cette méthode, appliquée de manière “naïve”, produit des images au rythme de la fréquence d’images de la séquence initiale. L’effet est frénétique, parce que l’image est entièrement réinterprétée par l’IA 30 fois par secondes.

En animation traditionnelle 2D, lorsqu’un personnage ne bouge pas, on est tenté de ne pas le redessiner à chaque image afin d’économiser du temps de travail. Le problème, c’est que le personnage reste alors complètement statique, ce n’est plus qu’une image fixe, ce qui peut parfois être perturbant au visionnage et faire sortir le spectateur de sa suspension d’incrédulité. Afin de conserver la sensation d’un personnage vivant, “animé”, les animateurs 2D ont donc souvent recours à une technique qu’on appelle ************Line Boiling************, qu’on pourrait traduire par “Ligne bouillante”. Ce procédé consiste à redessiner 2 ou 3 fois un personnage statique exactement dans la même position, en calquant simplement les traits du premier dessin. Ensuite, on met ces quelques dessins, qui paraissent exactement identiques, à la suite selon la fréquence d’images de l’animation en question, et les légères déviations, imperfections de la ligne, semble vibrer légèrement une fois en mouvement. Ainsi, même quand le personnage reste immobile pendant une longue période, il n’est pas nécessaire de le redessiner à chaque image, en faisant une boucle de quelques dessins identiques, on obtient une sorte d’animation qui naît de la différence entre les traits d’une image à l’autre.

Notre situation avec la génération d’images par IA est comparable, sauf que le problème est inverse. Pour nous, le problème n’est pas que le personnage soit trop statique, c’est qu’il ne soit justement jamais statique. Pour comparaison, c’est comme si on avait effectivement redessiné entièrement chaque image de la séquence. Notre analogie est compliquée par le fait que nos images ne soient pas dessinée sur une feuille blanche, mais générées par réinterprétation d’une image originale. Certains éléments de l’image originale sont plus ou moins préservés selon les paramètres déterminés pour la réinterprétation, comme la composition générale, le cadrage, le type de sujet (un visage, un objet, etc. ) et la position de celui-ci. Mais les détails, les couleurs, et l’aspect spécifique de l’image générée sont presque indépendants de l’image originale : dans l’exemple ci-dessus, même si le prompt était le même pour toutes les images, un personnage en style anime japonais avec des cheveux noirs, l’interprétation de chaque image a été radicalement différente, l’aspect des cheveux, la position des mèches, la présence ou non d’autres éléments autour de la figure centrale dans la composition, sont tant de données sujettes à des changements incontrôlables.

De manière générale, le problème principal de faire des films en images générées par intelligence artificielle est donc plutôt de **********stabiliser********** un résultat par nature instable, dont le mouvement est une sorte de clignotement plutôt qu’une continuité. Des amateurs de l’image générative ont redoublé d’inventivité pour créer des processus permettant de maximiser la stabilité de l’image. Cela pose un autre problème : si on utilise l’intelligence artificielle pour avoir accès à l’espace latent, le champ de tous les possibles (ce qui est quand même l’enjeu artistique le plus caractéristique de cette technologie), alors l’ambition de “fixer” l’image et de maintenir la cohérence temporelle la plus forte possible, va à l’encontre de ce que demande le medium même.

Faisant abstraction de cette ambivalence, on peut sans doute essayer de stabiliser autant que possible nos résultats en utilisant tous les outils disponibles avant de sélectionner plus précisément à quels endroits on souhaite laisser l’algorithme produire son indécision caractéristique.

Par exemple, en mai 2023, un étudiant en ingénierie informatique à Stanford publie un algorithme appelé ControlNet. Ce système contient des modules qui sont capables de décoder une image pour en extraire des données spécifiques utiles à la génération d’images, afin de rendre celle-ci plus précise et de rapprocher l’image générée de celle qui a été utilisée pour la créer.

### Environnement seul

![grid_controlnets.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/grid_controlnets.png)

De gauche à droite, l’image initiale, puis une version dont ont été extraits des segments qui représentent les contours de la structure, une autre dont la densité de noir représente la proximité de chaque élément par rapport à la caméra, et une dernière qui isole les éléments présents dans l’image selon leur type. Ces résultats peuvent être recombinés et envoyés avec un prompt et un modèle de diffusion, pour créer un résultat très précis:

![correspondingoutput.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/correspondingoutput.png)

On voit que les contours de la structure sont précisément respectés et que la composition reste la même. Le résultat est très proche de l’image initiale. Cependant, en utilisant une séquence d’images en mouvement, on observe que le changement d’image utilisée pour la génération des ControlNets modifie quand même l’aspect de l’image finale.

[Controlnetsequence_lowres.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Controlnetsequence_lowres.mp4)

On remarque que les ControlNets font tendre chaque génération d’image vers un résultat plus proche et plus précis que la diffusion standard de Stable Diffusion, mais qu’ils ne tiennent pas compte de la succession des images: ils traitent toujours chaque image indépendamment. Pour remédier à ce problème, il existe des méthodes à l’intérieur de Stable Diffusion, mais elles sont trop lourdes et peu pratiques. On peut plutôt utiliser un autre programme dédié au flux optique comme Ebsynth. Ce programme fonctionne en collant des images-clés sur une séquence d’images initiale, et en essayant de déplacer les pixels selon le mouvement sous-jacent.

Par exemple, on peut utiliser la première image qui a été générée par Stable Diffusion comme image-clé, et l’appliquer comme un style à l’ensemble de la séquence originale.

[4stepprogram.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/4stepprogram.mp4)

La vidéo du haut est la séquence initiale, les trois suivantes sont différentes manières de gérer la réinterprétation de cette séquence par une intelligence artificielle. Il s’agit en fait d’une gamme qui va du stroboscope au trip sous champignons. La “stabilité” selon ces critères est donc un positionnement sur ce spectre, un compromis entre la fréquence à laquelle l’image se reconfigure et la lisibilité de l’image dans le temps, sa cohérence temporelle.

La deuxième vidéo est située à l’extrême stroboscopique. Ici, ce qui nous intéresse, c’est la reconfiguration permanente de la maison au sein d’une structure d’image qui reste compréhensible. On pourrait décrire ce mouvement comme une marche à travers l’espace latent, chaque nouvelle image nous montre un possible sans jamais se fixer.

La troisième vidéo est située à l’extrême opposé, du côté psychédélique a un style fixé dès la première image, qui se détériore peu à peu à mesure que  le fond est emporté par les éléments de premier plan, et que des zones se dévoilent au cours du mouvement de caméra.

La quatrième vidéo se situe quelque part entre les deux, plus du côté trip psychédélique, mais en conservant l’idée que la maison ne soit jamais fixe, et toujours prise dans un flux entre deux états. Dès qu’elle semble être arrivée à une forme stable, elle se déstabilise. Mais la vidéo étant composée de 9 séquences imbriquées par des fondus enchaînés, ceux-ci sont très visibles, et donnent au tout un effet de superposition d’images qui est plutôt faible plastiquement.

Enfin, une dernière vidéo, ci dessous, en 4K, à l’aspect plus stable, avec beaucoup moins d’artéfacts, mais qui conserve une sensation de liquéfaction dûe au passage par Ebsynth, tout en contenant une transition assez lisse entre plusieurs états:

[Ebsynth_3keys_4K.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Ebsynth_3keys_4K.mp4)

Pour cette vidéo, on utilise beaucoup moins d’images-clés, ce qui permet des fondus enchaînés plus lents entre les séquences superposées, et donc moins proéminents.

Notes: La résolution à laquelle sont produites les images-clés nécessaires pour le passage dans Ebsynth est très basse (960x540 pour un format 16:9), sauf qu’ensuite, leur cohérence picturale est explosée par l’application du mouvement d’Ebsynth. Les images qui sortent d’Ebsynth ont été modifiées très fortement, ce qui influe sur la qualité de tout upscaling futur. Il serait donc souhaitable de travailler à partir de keyframes déjà upscalées en 4K ou FHD avant de les envoyer dans Ebsynth, avec des images à la résolution correspondante en input. Le problème, c’est que l vitesse de traitement d’Ebsynth est directement proportionnelle à la résolution des images utilisées: appliquer le mouvement à des images en 4K est beaucoup plus long que de passer par des sortes de proxys en basse résolution qui seront upscalés par la suite.

Le problème de la résolution est aussi un enjeu artistique, puisque les algorithmes qui augmentent la résolution ont tendance à modifier fortement la texture de l’image. La plupart des modèles risquent de lisser fortement l’image et lui donner un aspect plat et renforcer la sensation d’artifice à l’image. Tout dépend en fait de l’ordre de magnitude du changement de résolution. Si c’est une multiplication par 4, comme entre 960x540 et 3840x2160, la texture de l’image sera énormément lissée. Par contre, si il est possible d’appliquer une diffusion stable à une grille de 4 images FHD, on pourrait obtenir des images-clé d’assez haute résolution, qui nous permettraient de préserver l’aspect photographique souhaité en ayant une marge d’upscaling plus faible, en multipliant par 2 pour arriver à de la 4K.

## Environnement + personnage

### test 1: personnage diffusé par images-clés + Ebsynth

[eeveecomp_lowres.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/eeveecomp_lowres.mp4)

[ebsynth12keys_lowres.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ebsynth12keys_lowres.mp4)

[output.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/output.mp4)

Mais cette méthode est mal adaptée aux situations de vue d’ensemble ou le personnage se déplace dans un espace. En effet, à cause d’Ebsynth, son mouvement est lissé, ce qui nous fait perdre sa nature changeante. De plus, en se déplaçant, il a tendance à emporter le fond avec lui, ce qui crée une sensation liquide qui ne correspond pas tout à fait à l’histoire racontée.

Il faut donc appliquer la diffusion à chaque image, afin d’obtenir un résultat plus précis mais aussi plus hétérogène et étonnant visuellement.

Tests avec un personnage (960x540):

On commence par créer une séquence d’images filmées d’un personnage en mouvement, dont on a retiré le fond (par ex. avec rembg ou autre algorithme de masquage).

On importe cette séquence dans un logiciel de 3D, et on la positionne dans l’espace. Blender, Unity, peu importe: on déplace la caméra et on peut régler la lumière, mais le résultat final sera produit par Stable Diffusion, qui va appliquer comme un filtre aux images qui sortent brutes du programme 3D.

étant donné que la diffusion d’images avec des Controlnets prend du temps, on serait tenté d’appliquer la même méthode que pour le personnage facecam plus haut, en utilisant des grilles d’images-clés.

![00045-583161513.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/00045-583161513.png)

![00046-583161513.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/00046-583161513.png)

![00047-583161513.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/00047-583161513.png)

### Test2: Controlnet en FHD

[output.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/output%201.mp4)

[base_24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/base_24fps.mp4)

[controlnet_raw24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/controlnet_raw24fps.mp4)

[ebsynth_1key24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ebsynth_1key24fps.mp4)

[Ebsynth6keys24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Ebsynth6keys24fps.mp4)

[ebsynth_over_Controlnet_1key24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ebsynth_over_Controlnet_1key24fps.mp4)

[ebsynth_over_Controlnet_feathered_1key24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ebsynth_over_Controlnet_feathered_1key24fps.mp4)

[feathered_over_6keys_24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/feathered_over_6keys_24fps.mp4)

[feathered_over_base24fps.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/feathered_over_base24fps.mp4)

1. séquence de base exportée directement depuis le logiciel 3D (ou enregistrée en temps réel dans un moteur comme Unity)

2. Utilisation de Controlnets (MLSD + OpenPose + SEGMENTATION!!!) pour diffuser l’image en haute résolution (FHD) et obtenir un résultat très précis.

3. Ebsynth, en utilisant uniquement la 1ère image de la séquence, l’environnement se dégrade à mesure que le cadre change.

4. Ebsynth avec 6 images-clés réparties sur la séquence. Cela permet d’augmenter la stabilité à l’échelle de la séquence, mais le mouvement laisse trop transparaître la séquence originale sous-jacente (on reconnait l’image filmée dans l’image diffusée.

5. Incrustation du personnage, détecté par le ControlNet Segmentation, dans la séquence ebsynth avec 1 image-clé. Le résultat est intéressant, il distingue beaucoup plus le personnage de l’environnement, mais donne l’impression que ce premier a été photoshoppé dans l’espace.

6. Ici, on réutilise le même fond (la séquence Ebsynth générée à partir d’une image-clé) et on adoucit le masque qui sépare le personnage vers l’extérieur, comme ceci:
    
    ![maskdemo.png](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/maskdemo.png)
    
    [walking_shadow.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/walking_shadow.mp4)
    
7. Pour éviter la liquéfaction totale de l’environnement, on utilise la technique de l’étape 6. avec le masque adouci, mais en utilisant la séquence Ebsynth faite à partir de 6 images-clés, qui reste plus stable. L’adoucissement du masque d’opacité permet à la fois de préserver la sensation d’intégration du personnage dans l’environnement, en lui rendant son ombre par exemple, ainsi que de masquer les artéfacts et les glissements provoqués par le personnage dans la séquence Ebsynth (pour éviter ces artéfacts, on pourrait diffuser l’environnement sans le personage, mais cela retirerait l’ombre et l’intégration réaliste de celui-ci, et multiplierait les étapes sans garantir un meilleur résultat.
8. Enfin, on abandonne totalement Ebsynth: au lieu d’utiliser une version lissée, on multiplie le masque Controlnet avec la séquence d’images de base, ce qui permet de préserver certains détails. (En utilisant le mode de fusion multiplication, on gagne aussi un peu plus de contrôle sur la lumière, qui sera plus déterminée par la séquence de base, même si elle est nettement assombrie par le masque d’opacité du personnage.

On peut appliquer la même méthode aux plans en extérieur, pour isoler certains éléments qui “vibrent” dans un ensemble plus stable.

Pour que seule la maison réagisse aux mais en bas, la maison a été isolée sur un masque comme ceci:

[comparison_mask.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/comparison_mask.mp4)

Et le reste de l’image est la séquence de la maison stabilisée par ebsynth. Cela donne l’effet d’un travelling relativement stable (la séquence ayant été diffusée en basse résolution donne une texture un peu instable, mais en HD ça sera mieux), avec seule la maison qui se reconfigure en permanence.

Comparer avec:

[Controlnetsequence_lowres.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Controlnetsequence_lowres%201.mp4)

Version full Controlnet

[ebsynth3keys_lowres.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/ebsynth3keys_lowres.mp4)

Version Ebsynth lissée

[flickering_over_ebsynth_FHD.mp4](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/flickering_over_ebsynth_FHD.mp4)

D’autres tests avec un personnage qui se déplace dans un espace:

[ici, la séquence contient un décor en 3D qui est stylisé par Stable Diffusion + controlnet. L’image n’est pas mélangée à la séquence ebsynth, mais à l’image de base en 3D, dont est isolé le personnage par le masque. Cela permet de conserver beaucoup plus l’aspect original de la pièce, et les couleurs (j’utilise le mode de fusion “multiplication”, qui modifie les couleurs, et qui peut être ajusté). Le personnage est d’abord capturé par prise de vue réelle avant d’être passé dans stable diffusion + multi controlnet. Ensuite on utilise un depht pour lui donner tri-dimensionnalité relative plutôt qu’une image plane. Le personnage existe alors dans le décor, il réagit à la lumière ambiante etc.](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Controlnet_overbase_multiply.mp4)

ici, la séquence contient un décor en 3D qui est stylisé par Stable Diffusion + controlnet. L’image n’est pas mélangée à la séquence ebsynth, mais à l’image de base en 3D, dont est isolé le personnage par le masque. Cela permet de conserver beaucoup plus l’aspect original de la pièce, et les couleurs (j’utilise le mode de fusion “multiplication”, qui modifie les couleurs, et qui peut être ajusté). Le personnage est d’abord capturé par prise de vue réelle avant d’être passé dans stable diffusion + multi controlnet. Ensuite on utilise un depht pour lui donner tri-dimensionnalité relative plutôt qu’une image plane. Le personnage existe alors dans le décor, il réagit à la lumière ambiante etc.

[trop de flickering, mieux séparer le masque controlnet et ebsynth:](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/controlnet_base_ebsynth_multiplied.mp4)

trop de flickering, mieux séparer le masque controlnet et ebsynth:

[Ici, la séparation entre le personnage et le fond est plus claire. Les artéfacts sont causés par l’inexactitude du masque de segmentation de controlnet. On remarque aussi des glissements dans l’image dûs à Ebsynth.](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/weird_test2.mp4)

Ici, la séparation entre le personnage et le fond est plus claire. Les artéfacts sont causés par l’inexactitude du masque de segmentation de controlnet. On remarque aussi des glissements dans l’image dûs à Ebsynth.

L’idée est de maintenir le décor à un certain niveau de stabilité et que le personnage soit beaucoup plus foisonnant et polymorphe à l’intérieur de cet environnement. Pour donner cette sensation tout en évitant le côté “photoshoppé” qui peut résulter d’une simple intégration par masquage, j’ai modifié le masque d’opacité qui sépare le personnage, qui est sur le calque “Controlnet pur” du décor, sur la couche “Ebsynth/séquence de base (ces 2 couches étant stables, le mouvement se superpose parfaitement et permet d’utiliser des modes de fusion pour ajuster manuellement le degré de ressemblance à l’image initiale). Le masque d’opacité est flouté et étendu vers l’extérieur, ce qui lisse considérablement la bordure entre la zone Controlnet et la zone Ebsynth de l’image:

![mask_expand.jpg](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/mask_expand.jpg)

![matching_controlnet.jpg](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/matching_controlnet.jpg)

![matching_ebsynth.jpg](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/matching_ebsynth.jpg)

![matching_result.jpg](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/matching_result.jpg)

1. le masque d’opacité seul

2. l’image entière diffusée par Controlnet

3. l’image entière lissée par Ebsynth

4. la composition finale, qui mélange ces deux séquences selon le masque d’opacité. On peut ajuster facilement l’adoucissement du masque et sa taille.

L’effet produit par ce mélange personnage/espace est intéressant: le décor est stable, le personnage vacille, mais il a aussi une sorte d’aura, un halo autour de lui qui fait vaciller l’environnement qui l’entoure.

## NOTES ISMAEL

refs

workflow stable - ebsynth:

[https://www.youtube.com/watch?v=E33cPNC2IVU](https://www.youtube.com/watch?v=E33cPNC2IVU)

temporal consistency avec keyframes:

[https://www.youtube.com/watch?v=Adgnk-eKjnU](https://www.youtube.com/watch?v=Adgnk-eKjnU)

[https://www.youtube.com/watch?v=cEnKLyodsWA](https://www.youtube.com/watch?v=cEnKLyodsWA)

Chaîne YouTube : 

Ai and pixels 

Aitrepreneur 

**Robin Fernandes**

swap face : 

[https://youtu.be/A3uB0omvlDM](https://youtu.be/A3uB0omvlDM)

## Deepfake photo

### Best overall

D-iD (subscription price)

SAD Talker (SD) gratuit mais moins bien surtout les yeux

Hey Gen, payant, midrange quality

Revive (iphone) assez cool mais pas animé. effet photo.

**Relipsync** 

Wav2lip

**Text2speech + Realtime voice changer**

 TTS + RVC + 

chaque sentence à la main. 

Voice Cloning : 1 minute long, no background noise. 

Pro Voice cloning : Eleven Labs (easy)

2 mois pour l’avoir. 

très facile et bon. mais attention aux actions.