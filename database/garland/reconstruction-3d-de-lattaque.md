# Reconstruction 3D de l’attaque

## Version 1 - 4min20

Il y a parfois des mouvements un peu “sharp” quand la voiture change de direction, qui pourront être smoothés, les roues ne tournent pas et les arbres sont très moches, mais ça nous donne le temps réel accurate des événements.

**Déroulé** :

La voiture de UCE-1 démarre après une trentaine de secondes où il ne se passe rien, on voit seulement la voiture des terroristes qui passe avant que UCE-1 ne démarre, puis il sort du parking et et prend à droite sur la route, il fait un passage avec le centre sur sa gauche, puis demi-tour à l’intersection plus loin, et se fait bloquer par la voiture des terroristes sur le deuxième passage, conduit derrière eux sur 200m, ils se garent et la fusillade démarre. La vitesse des voitures est très approximative, mais les timings sont corrects dans la séquence des événements.

### Dashcam FBI

Vue depuis le tableau de bord de la voiture de UCE-1, qui nous donne l’aperçu de ce que lui même voyait en temps réel. Focale 30mm

[3D_FBI_Dashcam_FIXED_v20000-6240.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_FBI_Dashcam_FIXED_v20000-6240.mp4)

### Topshot

Plan en vue aérienne, plongant directement en bas avec la voiture de UCE-1 au centre. La caméra est verrouilée sur la voiture, à 100m de hauterur (focale 50mm)

[3D_FBI_Topshot_FIXED0000-6240.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_FBI_Topshot_FIXED0000-6240.mp4)

### Drone

Survol aérien avec un drone omniscient qui se déplace pour capturer l’attaque, à 75m du sol en focale 35mm

[3D_Drone_Flyover0000-6240.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_Drone_Flyover0000-6240.mp4)

[3D Attaque Garland (Animatic/Media forensics)](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D%20Attaque%20Garland%20(Animatic%20Media%20forensics)%209c9fecd1533b4f718e5fc702a6944725.csv)

## Version 2  - 4min14sec

Un peu mieux, avec des arbres qui bougent et les roues des voitures aussi

Manque encore le traffic, au moins avoir quelques bagnoles qui se promène, et l’anim dashcam est encore trop snappy

Pas de screenshake sur cette version, donc en plus c’est trop smooth…

[3D_Dashcam_V20000-6109.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_Dashcam_V20000-6109.mp4)

## Version 3 - 3min32sec

Avec screenshake, traffic, meilleure anim voitures

### Previz :

[3D_Dashcam_V3_PREVIZ1000-6109.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_Dashcam_V3_PREVIZ1000-6109.mp4)

### Rendu raytracing

Avec reflets, motion blur, et un glow pour les zones les plus lumineuses (pas d’exposition auto buggée, à garder pr une V4)

Le mouvement des voitures lors de la fusillade a été légèrement modifié depuis la Previz pour que les attaquants sortent plus tôt et que notre voiture accélère plus vite.

[3D_Dashcam_V3.mp4](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/3D_Dashcam_V3.mp4)

01:31 Hole on right hand side - Pickup truck on the left isn't properly aligned(rerender all while Pickup is in view to avoid snapping) to 01:35 (2184 -2280)
01:33 Floating cars on right hand side (2064-2424)
02:05 Slight hole on right hand side (2904 - 3144)
02:09 to 02:35 Big hole on right hand side - floating pickup (3000 - 3720)

OVERALL RERENDER :
2184 - 2424
2904 - 3720

### Rendu COMPRESSION ISMA - 200923

[Essai Compression Dashcam](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/Essai%20Compression%20Dashcam%20af99428609544105ab574af1d28ee575.md)

[dashcam_v3_210923-2210.mov](Reconstruction%203D%20de%20l%E2%80%99attaque%20e74620d265a8460e9c2f8a13c395fcb3/dashcam_v3_210923-2210.mov)