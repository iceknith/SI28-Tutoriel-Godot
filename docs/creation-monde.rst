Création du monde
=================

Initialisation du monde
-----------------------

Actuellement, on a un joueur, mais on n'a pas le monde dans lequel ce joueur doit se déplacer. Nous allons essayer dans le cadre de ce tutoriel de créer un monde qui ressemble à ça : 

.. image::img/ObjectifWorld.png

Dans le cadre de ce tutoriel nous travaillons avec des sprites (des dessins) qui sont de tailles 16 par 16. Cependant la résolution par défaut de godot (1152 par 648) est beaucoup trop grande pour ce type de sprite.
Dans la résolution par défaut de Godot, notre joueur ferait cette taille : 

.. image::img/contreExempleResolution.png

**Ce que vous conviendrait est un peu petit*.

Pour changer la résolution dans Godot, il suffit d'aller la modifier dans les paramètres du projet. Vous pouvez donc cliquez en haut à gauche sur ``Project`` puis sur projet settings.

..image::img/ProjectSettings.png

Vous allez voir une fenêtre qui ressemble à ça. Ne vous inquiétez pas, même s'il semble il y avoir beaucoup de choses, nous n'allons quasiment touché à rien.
Les paramètres de résolutions se situent dans l'onglet ``Window``.



Pour ce faire, on va commencer par créer une nouvelle scène qui sera notre `Monde`.
Cliquez sur **Scene -> New Scene** en haut à droite, ou sur le petit **+** en haut à côté de l'onglet de la scène ``player``, ou appuyez sur ``Ctrl+N``.
Une nouvelle scène vierge devrait s'ouvir:

.. image:: img/WorldCreation.png

.. hint:: Si vous êtes restés dans l'éditeur de code, vous pouvez revenir à l'éditeur 2D,
  en cliquant sur le bouton ``2D``, en haut de la fenêtre.

Ici, nous allons créer un ``Control Node``, c'est un type de Node qui permet de gérer la disposition de ses enfants sur l'écran. Pour ça, appuyez à nouveau sur le **+** et rechercher la node ``Control`` ou plus directement sur le boutton  ``User Interface`` dans la hiérarchie (en haut à gauche).
Vous pouvez renommer ce noeud en ``"World"``, et lui ajouter deux noeuds ``TextureRect`` en enfant.

Pour chacun d'entre eux, vous allez cliquer en haut 

.. warning::
  Depuis la version 4.3 de Godot, le nœud ``TileMap``, qui était jusque là utilisé, n'est plus d'actualité!
  Le fonctionnement est globalement similaire, mais faites bien attention à prendre un nœud ``TileMapLayer``.

.. note::
  Une tilemap sectionne le monde en une grille. Les cases de cette grille sont remplies avec des blocs que vous placez afin de construire le monde.
  Cette technique est très répandue dans les jeux 2D. Si vous avez joué à Mario Maker, concrètement, lorsque vous crééz un niveau, vous manipulez une tilemap.

Il s'agit de créer le monde en collant les uns aux autres des petits blocs de terrain, appelés `tiles`.
Ça permet non seulement de simplifier la création de niveau, mais ça permet également d'optimiser le jeu.

Customisation du TileMapLayer
-----------------------------

Nous venons de créer un ``TileMapLayer``, mais il ne contient pas encore de `tiles` à placer dans notre monde.
Pour ça, on va créer un ``TileSet``.

.. note::
  Un tileset, c'est un peu comme une palette en peinture.
  C'est là que seront stockés tous les blocs avec lesquels on va "peindre" notre monde.
  Le tileset contient non seulement les informations visuelles (à quoi ressemble le bloc), mais d'autres informations comme, par exemple, des informations sur la collision du bloc.

Pour ajouter un ``TileSet`` au ``TileMapLayer``, cliquez sur **Tileset -> New Tileset** dans l'Inspecteur.
Les onglets **TileSet** et **TileMap** devraient alors s'être ouverts dans la fenêtre du bas de l'éditeur.
Cliquez sur l'onglet **TileSet**:

.. image:: img/tilesetEmpty.png

Appuyez sur le bouton **+** **[1]**, cliquez sur **Atlas**, puis séléctionnez le fichier ``assets/tilemap/Tilemap_Flat.png``.
Godot va alors vous demander si vous voulez créer automatiquement des tiles dans l'Atlas.
Séléctionnez oui, et vous verrez une grille découper l'image en blocs de 16px par 16px.
Cependant, nous voulons des cases de 32px par 32px (la taille dépend de votre tileset, mais celui-ci a été dessiné pour des casses de 32*32).

.. image:: img/tilesetGridUncorrectSize.png

Pour régler ce problème, il faut changer la taille des `tiles`, les changeant de ``16px`` à ``32px``,
à la fois dans le ``TileMapLayer`` **[1]** et dans le ``TileSet`` **[2]**

.. image:: img/tilesetTilesSizeChange.png

Maintenant que vous avez créé votre tileset, vous pouvez aller dans l'onglet **TileMap**, pour "peindre" le monde.
Pour cela, il suffit de cliquer sur le bloc que vous voulez placer, et "peindre" votre monde dans l'éditeur.


.. Note Jules: Tout "corrigé" jusque là
.. + pour faire des titres, il faut les souligner entièrement, sinon ça fait des warning


Maintenant,

[temp]

- Ajout des murs
- Ajout du joueur dans ce monde