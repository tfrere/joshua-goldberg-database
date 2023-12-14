# Note Technique Projet Deepfake (Update October 2023)

<aside>
💡 Note sur les aspects technico-artistiques de Deepfake

</aside>

## 🎬 Monde Réel :

**I. Réel étrange** 

Le monde réel, tel que perçu à travers les yeux de Joshua, se manifeste sous une forme déréalisée, frôlant l'onirisme. Cette vision subjective est le cœur de notre démarche artistique, où la représentation du réel se voit intentionnellement altérée pour provoquer une familiarité troublante. L’ambition est de plonger le spectateur dans une atmosphère à la fois reconnue et étrange, suscitant une réflexion sur l'authenticité de l'image.

Pour concrétiser cette vision, nous optons pour une technique bipartite qui associe prises de vue réelles et éléments 3D, visant un rendu final singulier. Les personnages, filmés en prise de vue réelle, parfois séparément, seront réincrustés ultérieurement pour renforcer cette impression d'un réel légèrement décalé. La rotoscopie, appuyée par EB Synth et l'intelligence artificielle de Stable Diffusion avec des plugins tels que Multicontrolnet et Wav2lip, servira de toile à cette création. Un micro dataset, nourri de documents en lien avec Joshua, favorisera la création d'images hyperréalistes mais fluctuantes entre chaque frame, instillant un effet de morphing à la manière d'une animation, mais à une fréquence inférieure à 24 images par seconde. Notre démarche vise ainsi à immerger le spectateur dans une réalité biaisée, lui faisant explorer les confins d'un monde réel, mais déconcertant, à l'image des perceptions de Joshua.

> 🔍 **Exemple Prise de vue réelle + 3D + IA**
> 
> 
> 
> [ici, la séquence contient un décor en 3D qui est stylisé par Stable Diffusion + controlnet. L’image n’est pas mélangée à la séquence ebsynth, mais à l’image de base en 3D, dont est isolé le personnage par le masque. Cela permet de conserver beaucoup plus l’aspect original de la pièce, et les couleurs (j’utilise le mode de fusion “multiplication”, qui modifie les couleurs, et qui peut être ajusté). Le personnage est d’abord capturé par prise de vue réelle avant d’être passé dans stable diffusion + multi controlnet. Ensuite on utilise un depht pour lui donner tri-dimensionnalité relative plutôt qu’une image plane. Le personnage existe alors dans le décor, il réagit à la lumière ambiante etc.](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0/Controlnet_overbase_multiply.mp4)
> 
> ici, la séquence contient un décor en 3D qui est stylisé par Stable Diffusion + controlnet. L’image n’est pas mélangée à la séquence ebsynth, mais à l’image de base en 3D, dont est isolé le personnage par le masque. Cela permet de conserver beaucoup plus l’aspect original de la pièce, et les couleurs (j’utilise le mode de fusion “multiplication”, qui modifie les couleurs, et qui peut être ajusté). Le personnage est d’abord capturé par prise de vue réelle avant d’être passé dans stable diffusion + multi controlnet. Ensuite on utilise un depht pour lui donner tri-dimensionnalité relative plutôt qu’une image plane. Le personnage existe alors dans le décor, il réagit à la lumière ambiante etc.
> 

<aside>
💡 [Détail complet recherche workflow 3D + IA](Workflow%203D%20Stable%20diffusion%2008f1c680ab7344ceb8a37a96d99a44c0.md)

</aside>

> 🔍 **Exemple Prise de vue réelle + 3D + IA + Lipsync**
> 
> 
> [262439441-bb9d888a-d33e-4246-9f0a-1ddeac062d35 (1).mp4](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/262439441-bb9d888a-d33e-4246-9f0a-1ddeac062d35_(1).mp4)
> 
> Ici un exemple avec resynchronisation labiale.
> 

> 🔍 **Exemple Entraînement microdataset**
> 
> 1. Images réelles pour alimenter le dataset
> 
> ![IMG_4057.JPG](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/IMG_4057.jpg)
> 
> 1. images générées par Stable Diffusion, guidé par le prompt du microdataset
> 
> ![IMG_4053.JPG](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/IMG_4053.jpg)
> 

- **💡 En savoir plus sur Stable Diffusion**
    
    ![278888447-483fb86d-c9a2-4c20-997c-46dafc124f25.png](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/278888447-483fb86d-c9a2-4c20-997c-46dafc124f25.png)
    
    **Stable Diffusion** est un modèle d'intelligence artificielle conçu pour générer des images à partir de descriptions textuelles. C'est une forme de technologie appelée modèle de diffusion, qui commence par un motif de bruit aléatoire et le transforme progressivement en une image cohérente au fil de plusieurs étapes. Pendant ce processus, le modèle s'aligne sur les caractéristiques décrites dans le texte fourni, permettant ainsi de créer une image qui correspond à la description.
    
    Ce modèle utilise également des composants de l'apprentissage automatique comme **CLIP** (Contrastive Language–Image Pretraining), qui aide l'IA à comprendre et à associer des textes à des images. Cela permet à Stable Diffusion de produire des images qui sont non seulement visuellement impressionnantes mais aussi pertinentes au texte donné.
    
    **Stable Diffusion** est utilisé pour une variété d'applications, allant de la création artistique et du design à des applications plus pratiques comme la génération d'images pour des sites web ou des publicités. Sa capacité à créer des images détaillées et de haute qualité à partir de simples descriptions textuelles en fait un outil puissant pour les créateurs de contenu, les designers et les artistes.
    
    **Automatic1111** et **ComfyUI** sont deux interfaces utilisateur populaires conçues pour interagir avec le modèle **Stable Diffusion**.
    
    ![auto_new_demo-7cc62202fb39ed2f10854a404ad127db.png](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/auto_new_demo-7cc62202fb39ed2f10854a404ad127db.png)
    
    **Automatic1111** est une interface web qui permet aux utilisateurs de facilement générer des images avec Stable Diffusion. Elle offre une variété d'options et de paramètres pour affiner les résultats, et elle est appréciée pour sa simplicité et son efficacité.
    
    **ComfyUI**, quant à elle, est une autre interface qui se concentre sur une expérience utilisateur agréable et intuitive. Elle vise à simplifier l'interaction avec Stable Diffusion, rendant la génération d'images accessible même pour ceux qui ne sont pas techniquement inclinés.
    
    ![FsBPEdJWAAA2F_G.jpg](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/FsBPEdJWAAA2F_G.jpg)
    
    Les deux interfaces visent à rendre l'utilisation de Stable Diffusion plus accessible et plus conviviale.
    
- **💡 En savoir plus sur Control Net**
    
    ![1_yjvTQ1zwgPU-PkKy4Yf0Pg.png](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/1_yjvTQ1zwgPU-PkKy4Yf0Pg.png)
    
    ControlNet est un plugin complémentaire pour Stable Diffusion qui révolutionne la manière dont on peut générer des images. Contrairement aux outils standards de génération d'images qui offrent peu de contrôle sur la composition, ControlNet permet de copier des compositions d'image ou des poses de personnages à partir d'une image de référence avec une précision inégalée.
    
    Avec ControlNet, vous pouvez conserver la pose ou la position d'un personnage tout en générant une nouvelle image. Il peut également utiliser une "depth map" pour générer des images qui conservent les profondeurs de l'originale, permettant de modifier l'environnement ou l'ambiance tout en conservant les caractéristiques principales de l'image. Enfin, ControlNet peut transformer n'importe quel croquis en une œuvre d'art plus élaborée.
    
    Ce plugin change la donne en offrant plus de contrôle et de précision dans la création d'images, ouvrant la porte à de nouvelles utilisations innovantes.
    
- 💡 **En savoir plus sur Wave2Lip**
    
    Wave2Lip est un outil d'intelligence artificielle qui synchronise les mouvements des lèvres d'une vidéo avec un fichier audio donné. En d'autres termes, si vous avez un clip vidéo d'une personne parlant et un enregistrement audio séparé (qui pourrait être une autre personne parlant ou une version modifiée de la voix originale), Wave2Lip peut modifier la vidéo pour que les mouvements des lèvres correspondent à l'audio. Cela se fait grâce à un réseau de neurones profonds qui a été formé sur de nombreux exemples de personnes parlant.
    
    Pour l'utiliser, on fournit généralement à Wave2Lip deux entrées : la vidéo avec les mouvements des lèvres originaux et l'audio que l'on souhaite synchroniser avec la vidéo. L'algorithme analyse ensuite l'audio et génère de nouveaux mouvements des lèvres qui correspondent aux phonèmes et à la cadence de l'audio. Ces nouveaux mouvements des lèvres sont ensuite superposés sur la vidéo originale pour créer une illusion de parfaite synchronisation labiale.
    
    Il est important de noter que Wave2Lip et Stable Diffusion sont deux technologies distinctes. Stable Diffusion est un modèle de génération d'images basé sur des techniques de diffusion, capable de créer des images réalistes à partir de descriptions textuelles. Tandis que Wave2Lip se concentre spécifiquement sur la synchronisation labiale dans les vidéos.
    
    Ces technologies sont utilisées dans de nombreux domaines, tels que le doublage de films et de séries télévisées dans différentes langues, la création d'assistants virtuels plus réalistes, ou même la correction des erreurs de synchronisation labiale dans les enregistrements vidéo.
    
- **💡 En savoir plus sur EB synth**
    
    ![EbSynth-Advanced-Settings-Create-Glitch-Effects-with-EbSynth.webp](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/EbSynth-Advanced-Settings-Create-Glitch-Effects-with-EbSynth.webp)
    
    EbSynth est un outil de "style transfer" vidéo, c'est-à-dire qu'il peut appliquer le style d'une image clé à une séquence vidéo entière. En ce qui concerne son utilisation avec Stable Diffusion et ControlNet, EbSynth peut potentiellement être utilisé pour appliquer les images générées par Stable Diffusion et modifiées par ControlNet à une vidéo. Par exemple, si vous créez une image avec Stable Diffusion qui a un style artistique particulier, et que vous utilisez ControlNet pour ajuster la composition ou les poses, vous pourriez ensuite utiliser EbSynth pour appliquer ce style et ces modifications à chaque image d'une vidéo, créant ainsi une séquence animée cohérente avec le style et la composition désirés. C'est une façon de combiner les forces de ces outils pour la création de contenu vidéo enrichi et personnalisé.
    
- **💡 En savoir plus sur Animate Diffusion**
    
    Animate Diffusion est un outil qui utilise des techniques d'intelligence artificielle pour créer des animations fluides à partir d'images fixes. Il s'appuie sur des modèles de diffusion, comme Stable Diffusion, pour générer des images intermédiaires entre des cadres clés. Cela permet de transformer une série d'images statiques en une séquence animée cohérente et fluide. Animate Diffusion peut être utilisé pour animer des illustrations, des portraits, ou tout autre type d'images fixes, en leur donnant vie sous forme d'animations courtes et captivantes sans avoir recours aux méthodes traditionnelles d'animation image par image.
    

**II. Contenu altéré**

L'utilisation de DeepFaceLab et DeepFace Live permettra de modifier des prises de vue réelles existantes dans le but de créer des deepfake, qui sont la matérialisation des impersonations que Joshua avaient faite par texte. Elles seront ici sous forme vidéo, grâce à DeepFaceLab qui est un logiciel de référence en matière de création de deepfakes, reconnu pour sa précision et sa flexibilité. Quant à DeepFace Live, il offre la possibilité de réaliser des deepfakes en temps réel. Ces outils seront utilisés pour injecter une dimension nouvelle à des événements historiques, offrant ainsi un regard alternatif sur des instants déjà connus.

![deepfacelive_intro.png](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/deepfacelive_intro.png)

**III. Création d'Archives Fictives et esthétique forensique**

Pour certaines scènes de reconstitution forensique et aussi d’archives disparues ou manquantes, il sera nécessaire de réinterpréter artistiquement la matière documentaire. Pour cela, nous ferons appel à l'intelligence artificielle et à la modélisation 3D. Le rendu sera ensuite soigneusement retravaillé pour atteindre un degré de réalisme saisissant. Nous utiliserons des codecs vieillissants pour compresser les images et recréerons le style caractéristique d'une prise de vue amateur, afin d'imiter l'esthétique et les imperfections des archives d'époque.

- **💡 En savoir plus sur workflow Reconstitution archives**
    
    [Reconstruction 3D de l’attaque](../Garland%203c4b60b393d9465c8d145df1c604c7d6/Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3.md)
    

## 🌌 Univers des Forums :

Cet univers se présente comme une transposition en 3D des forums internet, semblable à un métaverse. Chaque espace reflète une communauté et une esthétique distincte, rappelant des jeux sociaux comme Second Life ou VR Chat. Certaines séquences seront enregistrées directement dans VR Chat ou GTA 6, tandis que d'autres seront créées à partir de décors conçus par nos soins. Nous mettrons en place un système de jeu et un serveur interactif, et les séquences seront enregistrées façon machinima. Les mouvements seront capturés via une combinaison Xsens ou [Move.ai](http://move.ai/), et les décors modélisés dans Blender avant d'être importés dans Unity ou Unreal. La stylisation finale se fera via Stable Diffusion en post-production.

> **🔍 Exemple de scène filmée dans VR Chat**
> 
> 
> [https://www.youtube.com/watch?v=9BbJVNiLVnU](https://www.youtube.com/watch?v=9BbJVNiLVnU)
> 
> Personnages controlés en direct, entièrement avec un équipement VR et une tenue mocap grand public
> 

## 🌀 Esthétique Clip pour les Séquences Oniriques :

Ces séquences serviront à représenter des états psychologiques intenses comme la folie d'internet ou l'anxiété générée par le harcèlement et les menaces de mort. Elles adopteront une forme polymorphique, psychédélique et angoissante, en utilisant notamment Deforum et Animate Diff, des plugins de Stable Diffusion, pour générer des vidéos à partir de texte ou modifier des images / vidéo déjà existantes.

- 💡 **En savoir plus sur Deforum et AnimateDiff**
    
    Deforum est un plugin pour Stable Diffusion qui offre une multitude d'options de personnalisation, permettant aux utilisateurs de préciser en détail comment ils veulent que leurs images soient générées. Il ajoute plus de 100 paramètres de configuration au carnet d'inference principal, permettant une grande variété de résultats et une personnalisation approfondie.
    
    Animate Diffusion, en revanche, est un outil conçu pour créer des animations à partir d'images fixes générées par des modèles de diffusion comme Stable Diffusion. Il fonctionne en générant des images intermédiaires entre des images clés pour créer une séquence animée fluide.
    
    La principale différence entre les deux est leur but: Deforum se concentre sur la génération et la personnalisation d'images fixes, tandis qu'Animate Diffusion est destiné à créer des animations à partir de ces images.
    

> 🔍 **Exemple de vidéo Deforum**
> 
> 
> [https://www.youtube.com/watch?v=BiYCnUGoBVQ](https://www.youtube.com/watch?v=BiYCnUGoBVQ)
> 
> [https://youtu.be/yWlIfDF79Y8](https://youtu.be/yWlIfDF79Y8)
> 
> [https://youtu.be/KSuiSjov5R8?si=mK_zONOpsbIFuDJz](https://youtu.be/KSuiSjov5R8?si=mK_zONOpsbIFuDJz)
> 
> Les vidéos sont à jouer en 0.75x
> 
> 🔍 **Exemple de vidéo AnimateDiff**
> 
> [https://x.com/rainisto/status/1709168141878640778?s=20](https://x.com/rainisto/status/1709168141878640778?s=20)
> 

## ✍️ Récapitulatif workflow :

![Capture d’écran 2023-11-01 à 02.33.12.png](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/Capture_decran_2023-11-01_a_02.33.12.png)

[DeepFake_Workflow_architecture_oct_23.pdf](Note%20Technique%20Projet%20Deepfake%20(Update%20October%20202%20eff67243e5d64c59a3a9bd41693174d3/DeepFake_Workflow_architecture_oct_23.pdf)

## 📸 Rendus & work in progress décors :

[Orange Park Renders](Orange%20Park%20Renders%20fea190a2735642eebcc1101e3db4193d.md)

[Joshua’s bedroom 3D model](Joshua%E2%80%99s%20bedroom%203D%20model%203cf88b8bcf164add900e9b68f550e839.md) 

[](Prison%203D%20model%205ede17a4989c440d9bf1d49557048890.md) 

[Screenshots 3D process (BTS)](Screenshots%203D%20process%20(BTS)%202f69a42d074a454e8e7ee82da7c843a4.md) 

## 🎥 Maquette film work in progress  :

[MATSUKI THE DREAMER 29_sept_0206_IJC pour EXPORT 1_good 1_rustin_isma-goodson](https://vimeo.com/878453331/4e06e7816d?share=copy)

## 📝 Conclusion :

Ce projet est une odyssée visuelle qui défie les conventions, brouillant les frontières entre réel et virtuel. Chaque technique et esthétique choisie vise à immerger le spectateur dans l'expérience subjective de Joshua, offrant une réflexion poignante sur la réalité digitale qui nous entoure.