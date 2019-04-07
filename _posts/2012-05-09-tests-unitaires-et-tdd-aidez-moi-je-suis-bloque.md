---
id: 304
title: 'Tests unitaires et TDD : Aidez moi ! Je suis bloqué !'
date: 2012-05-09T10:15:17+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=304
permalink: /tests-unitaires-et-tdd-aidez-moi-je-suis-bloque/
categories:
  - Agile
tags:
  - agile
  - agileFrance
  - conférence
  - tdd
  - testsunitaires
---

<img class="alignleft" title="Logo Agile France" src="https://2012.conf.agile-france.org/conf.agile-france.org/wp-content/themes/twentyeleven-agilefrance/images/AgileFranceConference2012-logo.png" alt="" width="153" height="153" /> Les 24 et 25 mai prochains, j&rsquo;animerai une session pas tout à fait comme les autres, que j&rsquo;ai intitulée : <a title="Session Agile France" href="http://2012.conf.agile-france.org/conf.agile-france.org/index260f.html?speakers=tests-unitaires-et-tdd-je-suis-bloque-aidez-moi" target="_blank">« Tests unitaires et TDD : Aidez moi ! Je suis bloqué »</a>. Lors de cette session, je proposerai au public quelques situations que j&rsquo;ai rencontrées dans ma démarche d&rsquo;apprentissage du TDD, voire du BDD, et d&rsquo;écriture de tests unitaires, et que je ne sais toujours pas très bien résoudre&#8230;<!--more-->


Vous l&rsquo;avez compris, ce n&rsquo;est pas moi qui apporterai la matière, c&rsquo;est-à-dire les réponses possibles à ces situations, mais le public ! Une session que je souhaite participative. Bien que je n&rsquo;aie jamais ni organisé ni même participé à ce type de session, je me suis lancé. Un peu dans la lignée de <a title="Le seul échec, c’est celui de ne pas apprendre" href="{{ site.baseurl }}/le-seul-echec-cest-celui-de-ne-pas-apprendre/" target="_blank">mes derniers billets de blog sur l&rsquo;importance de l&rsquo;échec</a>, j&rsquo;expérimente, je prend un risque, je me mets en danger&#8230; Car si effectivement, il n&rsquo;y a que peu de monde pour essayer de donner quelques éclairages, la session risque de ne pas durer très longtemps 🙂

Mais soit, depuis un certain temps je note quelques situations que j&rsquo;aimerais présenter. Mon but n&rsquo;est pas de les exposer ici. Et si vous avez l&rsquo;occasion de vous rendre à <a title="Agile France" href="http://conf.agile-france.org" target="_blank">Agile France</a>, et participer à cette expérience, vous pourrez les découvrir. De toutes façons, il n&rsquo;y a rien d&rsquo;extraordinaire, et la session est au niveau Ha de Shu-Ha-Ri (c&rsquo;est-à-dire moyen).

J&rsquo;ai aussi prévu de demander au public de soumettre quelques situations qui leur viendraient à l&rsquo;esprit. Le risque de cette session étant de ne pas avoir suffisamment de situations à proposer, je me suis dit que _**vous**_ faire participer, vous lecteurs de ce blog, pouvait être une bonne idée ! Cela vous permettrait d&rsquo;obtenir une ou plusieurs réponses à des questions que vous devez certainement vous poser comme moi, dans votre démarche d&rsquo;apprentissage. Donc allez-y ! C&rsquo;est ouvert !

Je ne vous promets pas de tout retenir, simplement parce que mon backlog n&rsquo;est pas vide, et qu&rsquo;il faut également que je m&rsquo;approprie votre problème pour le restituer au mieux le jour de la conférence. Si c&rsquo;est le cas, nous pourrons travailler sur un exemple qui mettra votre problème en situation et ainsi recueillir éventuellement des éclairages de participants. Pour vous lâcher, vous pouvez utiliser les commentaires, par mail, twitter, etc. Je ne manquerai pas, évidemment, de vous faire un retour une fois Agile France passé.

Edit : Comme me le suggère Xavier dans les commentaires, voici un ou deux exemples de situations que je vais proposer. Je ne vous révèle pas tout, sinon la session perd de son intérêt. Et si d&rsquo;aventure vous avez des solutions ou simplement des avis, merci de les mettre de côté  pour la session ou pour un peu plus tard :).

  * Méthode « passe-plat » : j&rsquo;ai par exemple une façade F, avec une méthode A qui encapsule simplement l&rsquo;appel à une méthode B d&rsquo;un collaborateur C, B ayant un nom différent de A, mais, admettons, les mêmes paramètres. Dois-je écrire un test unitaire pour A si je suis censé faire du TDD ?
  * J&rsquo;ai le sentiment qu&rsquo;une classe B sera nécessaire pour réaliser un traitement. La classe B sera utilisée par A, qui existe et doit donc évoluer. Dois-je d&rsquo;abord ajouter des tests à A et faire émerger B ? ou directement créer B en TDD puis le faire utiliser par A ?

Alors à vos contributions et merci de votre participation !

