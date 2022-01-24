---
date: 2022-01-22T16:00:0+01:00
description: "De flemme en motivation"
featured_image: "/images/letters_bg_1280.jpg"
tags: ["cms","golang","hugo"]
title: "C'est l'histoire d'un blog"
---

Toi qui es de passage en ce modeste lieu, tu te demandes sans doute ce que tu vas y trouver...
Il est en ce monde bien des sujets qui peuvent être abordés avec plus ou moins de succès.

J'avoue, un peu honteusement, qu'il ne s'agit que d'un morceau de jardin secret, ou plutôt un potager partagé.
En effet, pour peu que le cœur t'en dise,
j'aimerai planter des graines,
faire germer des idées en partageant avec toi quelques-unes de mes expérimentations, de mes pensées.

Tout voyage commence par un premier pas, partons donc simplement par la création même de ce coin de lecture. 
Si tu me permets une petite digression, dont j'ai peur d'être trop friand,
cela fait quelques années que je n'ai pris le temps d'ainsi publier.

D'abord vint l'idée,
elle n'était pas bien formée et manquait d'une volonté suffisante pour gérer un quelconque outil par mes propres moyens.
Mon regard se porta donc sur les plateformes bien connues, ici un [medium](https://medium.com/), là un [wordpress](https://wordpress.com/).
Je tentais, en vain, de me convaincre : l'important était l'exercice d'écriture, le chemin, et non la forme ou l'outil.
Cependant, une voix insistante me susurrait dans l'oreille : "un peu de courage, retire ta dextre du fondement".

Puis vint la motivation.
Il me fallait quelque chose de suffisamment technique pour être amusant,
simple pour ne pas y perdre trop de temps et gratuit pour ne pas y perdre trop d'argent.
Développeur de profession, je fis un rapprochement d'idées : puis-je gérer le blog comme je gère du code.
Je m'impose deux contraintes, garder le gestionnaire de sources et utiliser des technologies connues.
En somme, j'aimerai utiliser [Git](https://git-scm.com/) et [github](https://github.com/),
et trouver un [SGC](https://fr.wikipedia.org/wiki/Syst%C3%A8me_de_gestion_de_contenu) en [Go](https://go.dev/).

Bref, j'ai choisi sans trop de surprise [Hugo](https://gohugo.io/).
C'est un outil [open source](https://github.com/gohugoio/hugo) écrit en [Go](https://go.dev/) qui permet de générer des sites statiques.
Ça n'a l'air de n'être qu'un détail, mais il faudra un jour que je te parle du monde de l'[open source](https://fr.wikipedia.org/wiki/Open_source),
à la fois fabuleux et inquiétant, ouvert et impitoyable, ce sera l'objet d'une prochaine ballade.

Revenons à nos moutons, mais pour mieux comprendre la suite de notre voyage,
il faut que je t'éclaire sur le fonctionnement d'[Hugo](https://gohugo.io/).
Il s'agit d'un outil qui va prendre du contenu écrit en [markdown](https://fr.wikipedia.org/wiki/Markdown), 
utiliser un [modèle](https://gohugo.io/templates/) pour transformer tout ça en un site tout beau tout propre.
Tu l'auras compris, [Hugo](https://gohugo.io/) te fourni à la fois une base structurelle à personnaliser
et des outils de générations pour te mener au but ultime : la publication de ton site.

C'est bien joli tout ça, me diras-tu, mais du coup, comment et où le publie-t-on ce Blog ?
Effectivement, je peux stocker le contenu et la structure du site dans un dépôt [Github](https://github.com/),
mais où vais-je donc le publier ?
Il se trouve que [Github](https://github.com/) propose d'héberger des pages static via [Github Pages](https://pages.github.com/).

Je te vois venir, et tu as raison, je ne peux (décemment) pas mettre le contenu du projet Hugo dans le dépôt de [Github Pages](https://pages.github.com/).
La brique qui nous manque pour résoudre ce puzzle peut être fournie par une [intégration continue](https://fr.wikipedia.org/wiki/Int%C3%A9gration_continue).
Il s'avère, que [Github Actions](https://docs.github.com/en/actions) répond à ces attentes.

Bien, j'ai un dépôt d'édition/génération et un dépôt de publication.
Voyons comment je peux me dépatouiller de ce schmilblick.
Sur le dépôt de publication, j'active les [Github Actions](https://docs.github.com/en/actions) et je définis leurs comportements directement dans le dépôt concerné.
En utilisant leurs superpouvoirs, je dois [téléporter les sources](https://github.com/actions/checkout),
récupérer les [outils nécessaires](https://github.com/peaceiris/actions-hugo) à la génération,
transmuter la matière en site et [déployer](https://github.com/peaceiris/actions-gh-pages) pour [Github Pages](https://pages.github.com/).
Toutes ces incantations sont lisibles dans le [grimoire](https://github.com/jbdoumenjou/myblog/blob/main/.github/workflows/gh-pages.yml) du site.

Si la curiosité t'a poussée à lire les incantations de ce site, tu as pu détecter un peu de mysticisme, le mot de pouvoir `secrets.GH_TOKEN`.
De ta personne, tu devras l'imprégner afin que le sort n'agisse que pour toi, pour ce faire,
je t'encourage à consulter ce [document](https://docs.github.com/en/actions/security-guides/automatic-token-authentication).

Tu es toujours là ? Quel courage, quelle abnégation !
Nous arrivons au bout de cette aventure, enfin de la première étape.
Résumons en quelques mots :

* D'abord la définition du contenu et de l'allure grâce à [Hugo](https://gohugo.io/).
* Puis [Github](https://github.com/) pour stocker et profiter d'outils adaptés
  tels [Github Actions](https://docs.github.com/en/actions) pour transmuter les sources en site et le déployer auto-magiquement.
* Enfin [Github Pages](https://pages.github.com/) pour exposer le site publiquement.


Soyons honnêtes, ce n'est qu'une toute petite première pierre.
Il reste des éléments non traduits, des reliquats de thème par défaut, la structure est sommaire,
il manque la possibilité de faire des commentaires et bien d'autres choses.
Il s'agit tout de même d'une étape suffisante pour commencer à partager avec toi,
et d'ouvrir la voie pour de fabuleuses aventures (ou de petits égarements).

Je te laisse ici, en espérant te revoir bientôt !
Que les vents te soient favorable.
