---
id: 425
title: 'You&rsquo;re solving the wrong problem'
date: 2013-06-24T09:42:23+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=425
permalink: /youre-solving-the-wrong-problem/
excerpt_separator: <!--more-->
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
categories:
  - Agile
tags:
  - agile
  - fail fast
  - MacCready
  - Paul MacCready
  - pratiques
  - principes
  - qualité
  - tdd
---

<div style="width: 266px" class="wp-caption alignleft">
  <img class="  " alt="" src="https://upload.wikimedia.org/wikipedia/commons/9/92/Paul_maccready.jpg" width="256" height="204" />
  
  <p class="wp-caption-text">
    Paul MacCready et l&rsquo;anneau de vitesse
  </p>
</div>

La lecture d&rsquo;un article racontant l&rsquo;histoire de l&rsquo;ingénieur Paul MacCready, <a href="http://www.azarask.in/blog/post/the-wrong-problem/" target="_blank">article que vous pouvez retrouver ici</a>,  a été l&rsquo;un de ceux qui m&rsquo;a le plus marqué. Aujourd&rsquo;hui encore, je raconte cette fabuleuse histoire dans mes formations ou séminaires sur l&rsquo;Agile. Juste après le Marshmallow Challenge :). Je vous invite d&rsquo;ailleurs à la lire avant de poursuivre la lecture de ce billet.

Finalement, MacCready n&rsquo;a fait que s&rsquo;inscrire dans le principe du « _Fail fast, Fail safe_« . Sauf qu&rsquo;il l&rsquo;a fait pour construire un objet volant, avec une personne dedans, nous démontrant ainsi que ce principe peut réellement s&rsquo;appliquer partout, si tant est qu&rsquo;on fasse preuve d&rsquo;imagination et de bonne volonté.<!--more-->

## Redéfinir le problème

Dans cette histoire, qui justifie le titre de l&rsquo;article, repris pour ce billet, Paul MacCready, s&rsquo;est intéressé à la façon dont ceux qui l&rsquo;avaient précédé avaient tenté de gagner le concours. Et Paul en a conclu, de manière assez provocante, qu&rsquo;ils avaient tous échoué car ils avaient tenté de résoudre le problème posé, à savoir « faire voler un avion propulsé par la seule force humaine ». En réalité, MacCready critiquait le fait qu&rsquo;on essaye de résoudre le problème de manière trop directe.

La raison pour laquelle je raconte cette histoire juste après le Marshmallow Challenge est, pour moi, évidente. Dans les deux cas, les personnes qui se retrouvent face à leur problème n&rsquo;ont typiquement qu&rsquo;une vague idée de la solution qui pourrait marcher. Dans le cas du Marshmallow Challenge, j&rsquo;ai rarement deux équipes qui partent sur le même type de solution. Alors certes, au fur-et-à-mesure de faire faire cet atelier, des patterns émergent, mais dans la mise en oeuvre, et notamment l&rsquo;utilisation du scotch et du fil, il y a encore des divergences. Quand je demande si quelqu&rsquo;un dans l&rsquo;assistance a déjà mis un marshmallow au bout d&rsquo;une pate, pour voir comment résiste la pate, évidemment personne ne l&rsquo;a fait&#8230; Il en était de même dans l&rsquo;histoire de MacCready&#8230;

L&rsquo;apprentissage que j&rsquo;en retire, c&rsquo;est que quelque soit le domaine, quelque soit le sujet, si toute la solution ou simplement une petite partie est une inconnue, alors il est nécessaire d&rsquo;appliquer ce principe de « Fail fast, fail safe ». Quoiqu&rsquo;il en coûte. Dis avec les termes du Lean Startup, chaque hypothèse doit faire l&rsquo;objet d&rsquo;une validation, le plus tôt possible, amenant ainsi à décider de persévérer dans une voie, ou pivoter. Si on imagine une solution parfaite dès le début, ça peut marcher. Mais grâce à un extraordinaire concours de circonstances&#8230; Dans tous les autres cas, on aura déployé une énergie folle pour une déception inversement proportionnelle.

Plutôt que d&rsquo;essayer de résoudre le problème de manière directe, Paul MacCready nous indique qu&rsquo;il faut redéfinir le problème, ou plutôt résoudre un premier problème, dans son cas : comment créer un avion que l&rsquo;on peut modifier et refaire voler en quelques heures. Dans le cas du Marshmallow Challenge (attention spoiler ! texte en blanc à sélectionner pour le lire; ne lisez pas si vous n&rsquo;y avez pas encore joué) : <span style="color: #ffffff;">comment peut-on construire un édifice que l&rsquo;on peut rebâtir en quelques minutes, voire secondes ?</span>

Dans le cas de l&rsquo;informatique, je le vois de deux façons :

  * Sous l&rsquo;angle fonctionnel : comment peut-on faire pour construire une application que l&rsquo;on peut mettre en production plusieurs fois par jour ? Et ainsi obtenir le feedback nécessaire pour savoir si on va dans la bonne direction.
  * Sous l&rsquo;angle technique : comment peut-on faire pour construire une application qui ne fonctionne pas que « maintenant », et ainsi allonger sa durée de vie ?

## Livrer plus fréquemment

A mon sens, le problème n°1 dans l&rsquo;échec des projets ce sont les personnes et leurs interactions. C&rsquo;est peut-être aussi la raison pour laquelle c&rsquo;est la 1ère valeur du manifeste. La 2nde raison, c&rsquo;est que les projets sont trop gros. Beaucoup trop gros.

On cherche trop souvent à créer des mastodontes qui mettent des années à être développés avant d&rsquo;être livrés en catastrophe. La plupart du temps cela se passe en mode panique, puisque comme l&rsquo;heure de livrer approche (et qu&rsquo;on n&rsquo;a pas complètement fini), il faut vite le mettre à disposition pour le tester a minima, et le livrer à la date prévue&#8230; Et là, c&rsquo;est le drame ! Tout s’enchaîne ! Les gros bugs arrivent, des trucs évidents. C&rsquo;est lent. Très lent. Il faut qu&rsquo;un développeur assiste l&rsquo;équipe infra pour faire la mise en production. Au passage, le machin n&rsquo;est pas scalable : dès qu&rsquo;on crée deux nœuds load-balancés, ça ne marche pas. Et je passe encore l&rsquo;insatisfaction des clients qui se rendent compte que le truc fait tout, sauf ce dont ils ont besoin&#8230; Il semblerait que d&rsquo;après certains grands du web comme Amazon, Google et Microsoft, <a href="http://ai.stanford.edu/~ronnyk/2012-09ACMRecSysNR.pdf" target="_blank">seulement 10 à 30% des fonctionnalités que nous imaginons correspondent à un réel besoin</a>. Bref, c&rsquo;est un échec. Même si, au final, on a réussi à bricoler un truc&#8230; ça tient&#8230; comme au Marshmallow Challenge&#8230;

Stop ! You&rsquo;re solving the wrong problem ! Quand vous développez une application, pensez comme Paul MacCready. Redéfinissez le problème : Comment faire pour construire une application que l&rsquo;on peut mettre en production plusieurs fois par jour ?

Alors vous allez me dire « Mais des applications on en a développé des dizaines ! On sait faire maintenant ! ». Non ! Cette application-là, vous ne l&rsquo;avez pas développée avant. Pas de ce contexte, pas avec ces spécificités, pas avec ces technos, et pas avec ces personnes. Alors oui, il y a plein de choses que vous savez déjà, et qui à coup sûr vont vous faire gagner du temps. Mais c&rsquo;était le cas aussi pour MacCready : il savait pertinemment que pour voler, il allait falloir coller deux ailes à l&rsquo;appareil ! Maintenant, quelle taille devait avoir les ailes ? En quelle matière les construire ? Tout ça sont des questions auxquelles il dû répondre de manière empirique, son expérience l&rsquo;ayant aidé à trouver la bonne solution après plusieurs essais.

C&rsquo;est donc mon leitmotiv quand je démarre une application : « Comment faire pour être capable de mettre régulièrement (au claquement de doigts si vous voulez) l&rsquo;application en production ? ». Cette capacité, associé évidemment au fait de réellement mettre en production régulièrement, est un levier d&rsquo;apprentissage dont on a tort de se passer. Demain, faites l&rsquo;expérience : essayez de mettre votre application en production.

## Qualité durable

Notre culture dans le développement logiciel est encore très marquée par les approches traditionnelles. Cela se ressent même pour certains projets qui se veulent agiles. Même si on s&rsquo;organise en itérations, on a toujours en tête le mode de développement usuel, basé sur un développement initial suivi d&rsquo;une phase de maintenance. Généralement la phase de développement initiale est contrainte par le délai, le coût et, malgré tout, le périmètre. Cette culture nous a amené à livrer les choses à la va-vite, pour que ça marche à la date voulue. Et en bricolant, encore une fois, on y arrive.

Oui mais voilà, une fois livrée, l&rsquo;application doit vivre&#8230; et être maintenue&#8230; C&rsquo;est généralement là que les ennuis commencent : on paye le coût du bricolage effectué, sans lequel on n&rsquo;aurait peut-être pas respecté nos trois contraintes. J&rsquo;en ai vu quelques unes des applications qui n&rsquo;ont même pas tenu une année avant d&rsquo;être réécrite ! Et c&rsquo;est l&rsquo;application, donc les utilisateurs qui en patissent&#8230;

Encore une fois, on essaye de résoudre un problème qui n&rsquo;est pas le bon. Si on se pose une minute et qu&rsquo;on réfléchit comme Paul PacCready, le premier problème à résoudre est donc de savoir comment faire pour que l&rsquo;application n&rsquo;ait pas une durée de vie réduite. Posée autrement : « Comment faire pour construire une application dont le coût de modification reste faible **dans le temps** ? ».

Voilà pourquoi des principes ou pratiques comme TDD, l&rsquo;intégration continue, le refatoring, le design incrémental, les pratiques de Clean Code, etc., ont émergé. Elles contribuent fortement à aller dans ce sens. Car une fois ces bases posées, la construction de l&rsquo;application se fait plus sereinement, sans peur de tout casser. Alors j&rsquo;entends souvent dire que finalement tout cela est bien gentil, mais franchement, on n&rsquo;en a pas vraiment besoin&#8230; Je pense que ce genre de réflexion est soit prétentieuse, soit égoïste. Je n&rsquo;ai jamais entendu quelqu&rsquo;un dire cela en étant totalement convainquant&#8230; sauf justement pour des applications qui ont une durée de vie courte. Mais là n&rsquo;est pas le débat. Si aujourd&rsquo;hui je considère que ces pratiques sont indispensables, c&rsquo;est justement pour penser la qualité de l&rsquo;application dans le temps et non plus sur l&rsquo;instant. Et si demain de nouvelles pratiques émergent, et vont dans le même sens tout en étant plus performante, oui, je les adopterai.

## Un état d&rsquo;esprit

Certes, les exemples pris, notament dans la 1ère partie, nous montrent que le processus d&rsquo;apprentissage par l&rsquo;erreur ne suffit pas. Des compétences fortes, et couvrant tout le champ nécessaire à une réalisation, sont indispensables. C&rsquo;est indéniable.

Le problème c&rsquo;est qu&rsquo;aujourd&rsquo;hui, j&rsquo;entends trop souvent dire que ces compétences suffisent, que quelqu&rsquo;un de bon ne peut pas se tromper&#8230; Je n&rsquo;ai lu que très peu d&rsquo;histoires sur les génies qui ont marqué les différentes époques, mais tous ont rencontré à un moment donné des échecs, parfois retentissants ! Penser que l&rsquo;on est capable de faire bien du premier coup n&rsquo;est qu&rsquo;une forme de prétention&#8230; [qui mène au véritable échec : celui de ne pas apprendre]({{ site.baseurl }}/le-seul-echec-cest-celui-de-ne-pas-apprendre/ "Le seul échec, c’est celui de ne pas apprendre"). L&rsquo;expérimentation doit être la norme, et nous en sommes loin. Oui, pour construire une maison, il faut un plan. Mais demandez à un chercheur son planning de recherche de vaccin, avec toutes les tâches à effectuer. Nous ne faisons pas le même métier, j&rsquo;en suis bien conscient&#8230; tout comme le bâtiment en fin de compte&#8230; J&rsquo;ai pris sciemment ces exemples-là, car je pense que dans notre domaine, nous sommes à peu près entre les deux.

C&rsquo;est un véritable état d&rsquo;esprit à avoir. Cela ne s&rsquo;arrête pas à quelques pratiques. Dans le développement logiciel, cela veut dire : livrer plus fréquemment, et adopter des pratiques qui nous donnent un feedback continu sur la qualité intrinsèque du produit.

Si déjà nous arrivions à faire cela, je pense qu&rsquo;il serait beaucoup plus difficile pour des sociétés de conseil comme SmartView de continuer à vivre.

