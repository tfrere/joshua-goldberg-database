# Décors blancs

<aside>
💡 Pour faire le décor de la maison, je modélise dans Blender 3.5.1 avant import dans Unreal

</aside>

1. Je modélise en utilisant des shape très simple pour pouvoir les modifier facilement si jamais et avoir une idée de décor au plus vite. 
2. Je Unwrap mon mesh en smart UV unwrap
3. Je créé un matériaux qui va permettre de détailler mon mesh. Je l’applique  dans l’edit mode aux parties que je souhaite, et j’adopte le workflow suivant :
4. Dans le Shader node editor, je créer un texture adaptée en utilisant wave/noise/vonoroïde… branchée dans un colorramp branchée dans la surface de l’objet pour pouvoir la voir facilement.
5. Ensuite je branche le color ramp dans un bump node, lui même branché dans la normal d’un principal bsdf shader, avec une color base blanche. 
6. J’ajoute un image texture node branché à rien, dans lequel je créé une nouvel image 4k “Nomdel’objet_4K_Normal”.
7. Si j’ai plusieurs matériaux, j’ajoute ce nœud à chacun des matériaux, en prenant soin de le laisser sélectionné à chaque fois.
8. Je bake la normal de l’objet dans le render menu en, sélectionnant active “image texture” dans la target.
9. Je duplique mon objet pour ne pas perdre mes textures procédurales.
10. Dans le dupliqué, je supprime tous les matériaux pour en créer un nouveau. Je branche dans la surface l’enchainement suivant : *Principled BSDF > Image texture (avec normal map) > VectorMap > UV.*
11. Je peux exporter l’objet avec les réglages suivants : 

![to cc.PNG](De%CC%81cors%20blancs%202d0dc24e0dfe465da1e9a3e942f4ea6b/to_cc.png)