---
id: 297
title: De retour de Mix-IT Lyon
date: 2012-05-03T09:48:03+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=297
permalink: /de-retour-de-mix-it-lyon/
categories:
  - Agile
tags:
  - agile
  - conférence
  - mixit12
---

Jeudi dernier, j&rsquo;ai eu l&rsquo;occasion de me rendre à Lyon pour assister à Mix-IT, une conférence dédiées aux techologies liées à Java et au Web, et à l&rsquo;Agilité. Une conférence pendant laquelle j&rsquo;allais pouvoir enfin expérimenter certains jeux et surtout retrouver <a title="Agilité, Banyuls & Rugby : AOSud !" href="{{ site.baseurl }}/agilite-banyuls-rugby-aosud/" target="_blank">les collègues du dernier Agile Open Sud</a>.<!--more-->

Mon programme était centré sur les jeux, et notamment le Sky Castle Game d&rsquo;Antoine, Fabrice et Philippe, ou l&rsquo;expérience des billes de Rouges de Alexis « Deming » Monville. J&rsquo;avais également proposé <a title="mix-it LT " href="http://www.mix-it.fr/lightning/108/le-seul-echec-c-est-celui-de-ne-pas-apprendre" target="_blank">un lightning talk intitulé « Le seul échec c&rsquo;est celui de ne pas apprendre »</a>, et l&rsquo;ai donc soumis au vote du public. L&rsquo;ayant proposé assez tard je ne pensais pas qu&rsquo;il serait retenu, puisque seuls les 10 premiers l&rsquo;étaient. Il finira 6e ! 🙂

Et en préparant ma venue, une fois le calendrier publié, deux surprises :

  * La première était que j&rsquo;allais raté le Sky Castle Game : les lightning talks étaient prévus en même temps !
  * La deuxième était que Claire Blondel, dont je parle dans mon lightning talk, était prévue en keynote ! Cela allait me faciliter la tâche pour faire passer mon message !

## L&rsquo;expérience des billes rouges

C&rsquo;est un atelier auquel je vous conseille de participer. Là nous avions une heure et c&rsquo;était peut être un peu court. Pour ma part, j&rsquo;ai joué (très mal) le rôle de chef de la qualité. Je ne vous raconte pas le jeu, mais l&rsquo;idée est de mettre en avant les 7 maladies d&rsquo;une organisation et les 14 « points » de Deming. Expérience très intéressante, et donc trop courte. 🙂

## Backbone.js

Je ne voulais pas nécessairement suivre des sessions techniques mais finalement j&rsquo;ai suivi le flot&#8230; Tant qu&rsquo;à faire, autant apprendre quelque chose ! Même plusieurs choses puisque je ne connaissais ni Backbone ni CoffeeScript, langage utilisé lors de la démo.

J&rsquo;ai d&rsquo;ailleurs trouvé ce langage très intéressant, et sa syntaxe assez naturelle. Je ne sais pas si j&rsquo;ai bien compris, mais j&rsquo;ai l&rsquo;impression qu&rsquo;on peut s&rsquo;abonner à un événement « appel de méthode », du style messages.on(« reset », this.render, this);. Ce qui permet à une vue de réagir au changement du modèle (dans le cas de Backbone) ou de faire de l&rsquo;AOP. Intéressant&#8230; Mais je ne sais toujours pas si cela vien en effet de CoffeeScript, Underscore.js ou Backbone&#8230; Une idée ?

Backbone, lui, est un framework assez complet pour faire des applis Web assez facilement sur base de REST, Page-Controller, etc. A suivre donc&#8230;

## Lightning Talks

La déception de ne pas jouer au Sky Castle Game passée, je me suis rendu aux lightning talks. Et c&rsquo;est JB Dusseaut d&rsquo;Arpinum qui a démarré avec <a title="JB LT Mix-it vidéo" href="http://vimeo.com/41144268" target="_blank">« La voie du programmeur », que je vous invite à regarder</a>. C&rsquo;est cette session qui a eu le plus de voix lors du vote, et c&rsquo;était à mon sens effectivement la meilleure, mais je vous laisse vous faire votre idée.

J&rsquo;ai bien aimé aussi le concept de Developer Experience (DX) présenté par Pamela Fox. L&rsquo;idée est que de la même façon qu&rsquo;on fait de l&rsquo;UX pour l&rsquo;interface, il faut faire du DX lorsqu&rsquo;on conçoit une API ou un framework. L&rsquo;idée est de rendre son utilisation la plus naturelle possible.

Puis au bout de quelques unes, c&rsquo;était à mon tour&#8230; quel stress ! J&rsquo;ai déjà donné des sessions classiques d&rsquo;une heure. Mais là le format 5 minutes, faut pas se planter sinon c&rsquo;est mort ! On verra bien au montage le rendu final, mais je n&rsquo;étais pas totalement satisfait. Soit, ce n&rsquo;était qu&rsquo;une expérience de plus dont j&rsquo;essayerai de tirer les enseignements 🙂 (sujet du discours). Si vous voulez la version développée en attendant la vidéo, <a title="Le seul échec, c’est celui de ne pas apprendre" href="{{ site.baseurl }}/le-seul-echec-cest-celui-de-ne-pas-apprendre/" target="_blank">suivez ce lien</a>.

Enfin celui d&rsquo;Alexis Monville m&rsquo;a bien plus. Plus que le fond, avec lequel je suis totalement en phase, j&rsquo;aime bien la façon dont Alexis présente les choses, en posant des questions, et en laissant parfois des grands blancs. Le message passe mieux que quelqu&rsquo;un qui parle en flux continu (comme moi) et où finalement on retient moins de choses.

## L&rsquo;Agile chez Google

Je ne sais pas si je me suis rendu à cette session parce que c&rsquo;était Google, ou parce que c&rsquo;était Petra Cross&#8230; 🙂 En tout cas, elle sait faire en sorte que son auditoire l&rsquo;écoute religieusement ! 🙂 Avec JB, on s&rsquo;est calé dans des transats disposés dans le couloir, vu que la salle était pleine. Il ne manquait qu&rsquo;un petit pastis 🙂

Pour en revenir au sujet, rien de très extraordinaire chez Google. Google semble être agile. Bonne nouvelle ! Evidemment ils ne font pas de Scrum, mais plutôt du Kanban, même s&rsquo;ils planifient toutes les semaines. D&rsquo;ailleurs cela m&rsquo;a poussé à me poser cette question : peut-on faire autre chose que du Kanban lorsqu&rsquo;on déploie continuellement, plusieurs fois par jour ? Ils font aussi un peu d&rsquo;XP, mais pas tout&#8230; (RIP Antoine, JB, Thierry, Sylvain, etc. 🙂

Un sujet qui m&rsquo;a marqué est la volonté de Google de limiter le plus possible le temps de réunion. Cela se traduit par des réunions de planif de 30 minutes max, des rétrospectives hebdomadaires de 15 minutes, assez efficaces, mais aussi par l&rsquo;abandon des daily standups, considérés uniquement comme un outil pour les managers. Je retiens cette idée de vouloir rendre les réunions plus efficaces. En revanche, la rétro de 15 min me parait trop courte, ou alors avec une sacré expérience. L&rsquo;abandon des daily standups va trop loin à mon sens. Surtout qu&rsquo;il est perçu comme un outil pour les managers, or ce n&rsquo;est pas son rôle. Personnellement, je remets pas mal en cause le fameux format des 3 questions. Non pas les questions elles-mêmes mais le fait qu&rsquo;elles soient posées individuellement. Elles sont parfois mal comprises, et utilisées pour du reporting. Or ce n&rsquo;est absolument pas leurs rôles. Dans le même esprit, je commence à chercher une façon d&rsquo;abandonner les points pour les estimations&#8230;

## Le DotGame

Je me suis ensuite précipité pour aller jouer au Dot Game d&rsquo;Oana Juncu. L&rsquo;idée est de fabriquer des pizzas et mettre en oeuvre les principes du Kanban. La base est très intéressante. On s&rsquo;est pour le coup bien amusé. Je suis resté toutefois un tout petit peu sur ma faim pour plusieurs raisons :

  * Le jeu ne tient pas en pas en 1h ou alors en limitant le nombre d&rsquo;itérations. Il y a à mon sens un temps minimum de rétrospective entre les itérations qui est nécessaire, sans lequel on peut avoir du mal à apprendre pendant le jeu.
  * Une rétrospective finale a aussi manqué, mais par manque de temps là encore.
  * En fait, on est dans le vrai Kanban, celui de Toyota. Donc il faut aller au bout. Et son objectif est plus de faire de la qualité totale que d&rsquo;aller vite. Or là on était purement dans de la précipitation, sans prendre en compte la qualité. Je pense qu&rsquo;il devrait y avoir des critères plus stricts là dessus. Car soyons clair : ce qui donne le sentiment d&rsquo;aller plus vite, c&rsquo;est que la qualité est obtenue du premier coup !

En tout cas, toutes ces raisons me poussent à y rejouer !

## Anatomie d&rsquo;une mission agile

Enfin, je suis allé écouter religieusement et boire les paroles de Pablo lors de cette session que je connaissais déjà, et que je vous invite à voir. L&rsquo;exercice n&rsquo;est pas simple car c&rsquo;est un retour d&rsquo;expérience d&rsquo;une mission de coaching par le seul coach (en l&rsquo;absence du client). Cela peut parfois être interprété comme une volonté de se mettre en avant en faisant la part belle aux réussites.

Mais ce n&rsquo;est pas le cas de cette session. Elle vise simplement à alerter qu&rsquo;une transition agile, quelle qu&rsquo;elle soit, n&rsquo;est pas simple ni de tout repos, et qu&rsquo;elle nécessite une prise de recul que seul quelqu&rsquo;un qui a vécu plusieurs expériences peut amener. Attention, on peut prendre un coach, mais on peut aussi embaucher ! Sur la forme, après avoir vu les prémisses de cette session, le discours de Pablo est aujourd&rsquo;hui arrivé à maturité, ce qui est finalement on ne peut plus normal après plusieurs expérimentations.

## Des rencontres, des retrouvailles

Voilà donc une journée bien remplie, jalonnée de discussions sur des sujets plus ou moins sérieux avec quelques personnes de la communauté. On s&rsquo;est bien marré, et ça donne forcément envie de se retrouver ! Rendez-vous lors de prochains événements, Agile France fin mai à Paris et, peut-être, Agile Innovation à Lyon au mois de juin !

