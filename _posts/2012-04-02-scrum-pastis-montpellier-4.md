---
id: 264
title: 'Scrum Pastis Montpellier #4'
date: 2012-04-02T10:48:07+02:00
type: blogpost
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=264
permalink: /scrum-pastis-montpellier-4/
excerpt_separator: <!--more-->
categories:
  - Agile
tags:
  - agile
  - dailyscrums
  - legacycode
  - scrum
  - scrumpastis
---

Ce jeudi avait lieu notre 4e Scrum Pastis Montpellier. L&rsquo;occasion pour moi de faire un retour sur les discussions auxquelles j&rsquo;ai participées, mais également de revenir sur le démarrage de ces Bar Camps lancés il y a 4 mois, après l&rsquo;Agile Tour Montpellier.<!--more-->

## Une bonne dynamique

Les Scrum Pastis sont partis d&rsquo;une discussion entre plusieurs membres de l&rsquo;organisation du 1er Agile Tour Montpellier. Il y avait une volonté de fédérer la communauté et profiter de l&rsquo;événement pour créer une dynamique. Après quelques réflexions autour de l&rsquo;intérêt d&rsquo;une association, nous avons simplement décidé de lancer une première rencontre sur le modèle Bar Camp.

Le nom, lui, a été trouvé lors d&rsquo;une discussion juste avant l&rsquo;Agile Tour Marseille, où le nom a été lancé sous forme de blague. Il existait les Scrum Beer parisienne (je dis ça pour que mes copains toulousains me hurlent dessus), les Scrum Wine bordelais, il y aura maintenant les Scrum Pastis Montpellier ! (quid des Scrum Chouchen, Scrum Choucroute, etc ?)

L&rsquo;organisation est assez simple : on se rassemble sur un lieu, on propose et on choisit des sujets, puis on lance quelques groupes de discussion. La dynamique est intéressante puisque l&rsquo;on est monté à 20 personnes ! On espère maintenant conserver ce rythme !

Jeudi dernier, nous avons été accueillis par Lexik, dans ses locaux, pour la 2e fois. J&rsquo;en ai profité pour discuter de deux sujets très chauds pour moi en ce moment :

  * Comment dynamiser les Daily Scrums ?
  * Code legacy : la poule ou l&rsquo;oeuf ?

## Dynamiser les Daily Scrums

C&rsquo;est marrant que ce sujet soit ressorti jeudi, car j&rsquo;avais lu le jour-même des choses qui allaient dans le sens de mon expérience. Mais revenons au sujet. Le problème que posait ce sujet à la personne qui l&rsquo;a proposé était qu&rsquo;il avait le sentiment que les Daily Scrums tournaient au rapport de travail effectué, de justification du temps passé, et que dans le même temps, il ne remplissait pas réellement son rôle de synchronisation.

C&rsquo;est exactement le sentiment que j&rsquo;ai aujourd&rsquo;hui dans l&rsquo;équipe dans laquelle j&rsquo;évolue. Les gens se sentent obligés de justifier pourquoi ils n&rsquo;ont pas été là la veille, ou parler de choses qu&rsquo;ils ont faites et qui n&rsquo;ont pas de rapport direct avec le produit. Pire : ceux qui ne sont pas là envoient un email aux autres, et ceux qui sont là se sentent obligés d&rsquo;envoyer un email en retour avec le récapitulatif de ce qu&rsquo;il s&rsquo;est dit. Cela part d&rsquo;une bonne intention, et peut parfois être utile, mais là ça tourne totalement au rapport d&rsquo;activité. Comme je le tweetais le jour même, je me rends compte en plus que le moment où je décroche, c&rsquo;est lorsque que l&rsquo;on parle d&rsquo;un point particulier qui concerne « l&rsquo;autre » produit&#8230; Mais ma position ne me permet pas de d&rsquo;amener des changements importants à ce niveau. J&rsquo;y vais donc par petite touche.

Donc un sujet chaud pour moi, vous l&rsquo;aurez compris. Et ce qu&rsquo;il est ressorti de la discussion, ce sont les points suivants :

  * le faire debout et face au tableau (et pas à la pause clope !)
  * s&rsquo;en tenir au daily scrum produit par produit (s&rsquo;il est encore besoin de le préciser)
  * bien timeboxer le daily scrum (là encore s&rsquo;il faut le préciser&#8230;), quitte, au début, à afficher un décompte
  * une façon de le rendre plus dynamique est d&rsquo;utiliser un ballon ou tout autre objet qui permet de passer la parole à quelqu&rsquo;un. Qui plus est, cela peut mettre un peu de fun et décomplexer 🙂
  * enfin, moi j&rsquo;opte pour l&rsquo;abandon des trois questions au profit des User Stories : il faut se concentrer sur la Valeur.

Ma petite expérience sur le sujet m&rsquo;a montré que les 3 questions habituelles ont tendance à générer une nécessité de justification. La valeur « transparence » de Scrum a aussi tendance à être assimilée au flicage. Personnellement, j&rsquo;avais commencé à changer ma façon de faciliter les daily scrums dans une mission précédente. Je souhaitais que l&rsquo;équipe parle des User stories, et qu&rsquo;ils se disent à la fin du DS s&rsquo;ils étaient toujours confiants par rapport à l&rsquo;engagement de début de sprint et au but du sprint. Et pour en revenir à ce que je disais au début, c&rsquo;est jeudi que je suis tombé sur <a href="http://www.scrum.org/storage/scrumguides/extension/Feature-Focused%20Daily%20Scrum.pdf" target="_blank">ce document venant de personnes de scrum.org</a>. Et quoique la description est un peu pompeuse et pénible à lire, je suis favorable à cette évolution. A vous de voir, mais pour moi ce qui compte, ce n&rsquo;est pas ce que les gens ont fait de leur journée, c&rsquo;est « est-ce qu&rsquo;on produit toujours de la valeur de manière efficace (ie sans blocage) ? ».

## Code legacy : la poule ou l&rsquo;oeuf

C&rsquo;est un sujet <a href="{{ site.baseurl }}/agilite-banyuls-rugby-aosud/#codelegacy" target="_blank">auquel j&rsquo;avais déjà participé lors du dernier Agile Open Sud</a>. La question était cependant légèrement différente : doit-on commencer par poser des tests avant de refactorer ? Où peut-on commencer quelques actions de refactoring sécurisées pour rendre l&rsquo;application plus testable ? Nous sommes donc restés sur l&rsquo;aspect technique de la question. Il semble qu&rsquo;effectivement la réponse n&rsquo;est pas unique, et dépend de la qualité initiale. Mais dans notre cas, on parlait d&rsquo;une application réellement de mauvaise qualité et sans test.

Deux d&rsquo;entre nous avions déjà une expérience sur le sujet. Tous deux avons eu la même stratégie qui a consisté à commencer par poser des tests et mettre en place une infrastructure d&rsquo;intégration continue. Etant donné le manque de testabilité de l&rsquo;application, nous nous sommes vite tournés vers des tests UI. Ils peuvent être très coûteux à mettre en place, surtout sur des applications client lourd, et quand on ne maitrise pas les frameworks ou outils de test comme c&rsquo;était mon cas (White, NDLR). Mais comparé à la dette accumulée, cela reste largement raisonnable.

Après il convient de mettre en place quelques techniques. Pour ma part, je commence par mettre des façades et casser les dépendances encapsulées par ces façades. Le fait de mettre en place de l&rsquo;injection de dépendance va me permettre de commencer à poser des tests de « code » (unitaires ou intégration selon les cas&#8230; on est dans du code legacy !). Il faudra un jour que lise le bouquin « Working with legacy code » de Michael Feathers pour compléter mon approche.

## Prochain Scrum Pastis sur le thème des jeux

Une soirée intéressante donc, où nous étions moins nombreux que pour les deux derniers, mais où nous avons pu accueillir de nouvelles personnes. On a également parlé du fait que le nom « Scrum Pastis » rebutait certaines personnes de peur que l&rsquo;on ne parle que de Scrum. Certainement une amélioration à ce niveau-là.

Enfin, nous avons évoqué le prochain Scrum Pastis consacré aux innovation/agile/serious games, histoire de redynamiser ces Bar Camps, et éviter la routine. Je pense qu&rsquo;on l&rsquo;accueillera même chez Smartview. Stay tuned !

