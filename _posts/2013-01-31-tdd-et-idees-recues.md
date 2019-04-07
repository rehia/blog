---
id: 367
title: TDD et idées reçues
date: 2013-01-31T10:02:08+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=367
permalink: /tdd-et-idees-recues/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
categories:
  - Agile
tags:
  - agile
  - tdd
---

[<img class="alignleft size-medium wp-image-372" alt="idee recue" src="http://blog.avoustin.com/wp-content/upload/idee-recue-300x219.png" width="300" height="219" srcset="http://blog.avoustin.com/wp-content/upload/idee-recue-300x219.png 300w, http://blog.avoustin.com/wp-content/upload/idee-recue.png 450w" sizes="(max-width: 300px) 100vw, 300px" />](http://blog.avoustin.com/wp-content/upload/idee-recue.png)Après une tournée qui m&rsquo;a mené aux Agile Tour de Marseille et Bordeaux, j&rsquo;ai éprouvé le besoin de faire un peu le point sur TDD, ou en tout cas sur ma compréhension de TDD. Je pense en effet qu&rsquo;il y a quelques idées reçues sur cette pratique qu&rsquo;il faut assez vite dépasser au risque de ne pas arriver à la maîtriser  C&rsquo;est encore loin d&rsquo;être le cas pour moi, mais à défaut, je pense qu&rsquo;il faut avancer sur les bons rails pour progresser.

<!--more-->

## TDD n&rsquo;est pas qu&rsquo;une pratique

Dans cette petite introduction, je présente TDD comme une pratique, car c&rsquo;est ce qu&rsquo;elle est de prime abord. Mais le côté pratique de TDD n&rsquo;est que la partie visible de l&rsquo;iceberg. Derrière se cache un réel mode de pensée, qui s&rsquo;appuie sur le feedback et l&rsquo;échec rapide (« Fail fast, Fail safe ») chers à nos esprits obnubilés par l&rsquo;expérimentation. Je n&rsquo;ai pas choisi le terme « obnubilé » par hasard, car il y a dans l&rsquo;esprit d&rsquo;un pratiquant du TDD une impression de vide assez maladive lorsque des tests sont rouges. A tel point que n&rsquo;ajouter des fonctionnalités qu&rsquo;au « feu rouge » et pas à un autre moment devient une vraie discipline. Et ce mot « discipline » (merci JB !) prend bien plus de valeur et de sens que celui de « pratique ».

## TDD n&rsquo;est pas une façon de tester son code

Oubliez tout de suite cette idée reçue, malheureusement trop répandue. D&rsquo;ailleurs le terme « Test Driven Development » nous l&rsquo;explique clairement. L&rsquo;objet de cette discipline, donc, n&rsquo;est pas le test, mais bien le développement. Les tests ne sont qu&rsquo;un moyen pour développer. J&rsquo;irai plus loin en disant que les tests sont un moyen de concevoir du code. En cela je préfère parler de « Test Driven Design ».

Le fait que les tests que l&rsquo;on écrit au fur-et-à-mesure de nos cycles servent à la non-régression n&rsquo;est presque qu&rsquo;un effet de bord. On ne cherche pas à tester de manière exhaustive lorsqu&rsquo;on fait du TDD. On cherche juste à s&rsquo;appuyer sur un test pour progresser dans l&rsquo;ajout de fonctionnalités et, donc, le design du code. Cela ne veut pas dire qu&rsquo;il faut laisser des cas en chemin.

En faisant du TDD, on cherche à se rassurer, à augmenter notre niveau de confiance dans le code écrit. Et c&rsquo;est d&rsquo;ailleurs le seul indicateur valable, bien qu&rsquo;il ne soit pas chiffrable. En parlant d&rsquo;indicateur chiffrable, on demande souvent quel niveau de couverture on doit obtenir quand on fait bien du TDD. Ma réponse est que je peux avoir un code 100% couvert, comme ce « doit » être théoriquement le cas, et ne pas être confiant vis-à-vis de mon code, ou avoir juste 80-85% et avoir un niveau de confiance suffisant.

Donc si j&rsquo;estime avoir un doute sur un cas précis, je n&rsquo;hésite pas à écrire le test qui correspond. Pour réduire ma peur, et augmenter ma confiance.  
Enfin, TDD est aussi une très bonne technique pour apprendre. Par exemple, si j&rsquo;utilise un framework dont je ne connais pas le comportement dans certains cas, je vais écrire un ou plusieurs tests sur le framework pour comprendre son comportement. Peut être que ma première assertion sera fausse, mais au fur et à mesure, je comprendrai mieux ce qu&rsquo;il faut faire pour arriver à mes fins.

## TDD remplace toute activité de conception

Ça aussi, c&rsquo;est une idée reçue. Quand on démarre une session de TDD, il est important d&rsquo;avoir bien son objectif en tête, car c&rsquo;est cela qui nous mène jusqu&rsquo;à la solution. Parfois la solution vient s&rsquo;inscrire dans un ensemble plus grand, et il peut être intéressant de faire une petite session de quick design, pour se positionner dans cet ensemble, et notamment voire ce que l&rsquo;on peut réutiliser ou faire évoluer. Maintenant, rien ne sert de partir dans une grande documentation de conception détaillée qui n&rsquo;apportera pas de plus-value. Des tests bien clairs et lisibles, accompagnés éventuellement d&rsquo;un petit diagramme de CRCs, suffisent amplement&#8230; normalement&#8230;

Idem, rien ne vous empêche de réaliser un petit manuel de l&rsquo;API que vous avez faites (s&rsquo;appuyant sur le diagramme), mais en ne couvrant pas tous les petits détails, puisque les tests sont là pour ça. En revanche, si vous faites du TDD correctement, vous devriez drastiquement réduire vos temps de debugage. C&rsquo;est d&rsquo;ailleurs un excellent indicateur (qu&rsquo;on peut mesurer qui plus est), car plus vous avez à debuguer, plus vous devez améliorer votre pratique du TDD.

## TDD remplace les activités de test traditionnelles

Comme je l&rsquo;ai déclaré plus haut, TDD n&rsquo;est pas une façon de tester. Ça veut donc dire qu&rsquo;il faut tester par ailleurs. En revanche, il y aura un impact sur la stratégie de tests a posteriori, car les tests que l&rsquo;on amène avec notre mise en oeuvre du TDD vont couvrir des cas qu&rsquo;il ne servira peut-être à rien de couvrir par d&rsquo;autres types de test. On cite régulièrement <a title="Pyramide de tests Mike Cohn" href="http://www.mountaingoatsoftware.com/uploads/blog/Testpyramid.jpg" target="_blank">la pyramide des tests de Mike Cohn</a>. Elle donne un bon aperçu de ce qui peut être fait. Ou encore <a title="Quadrant des tests Brian Marick" href="http://lh3.ggpht.com/_X3kaawac_g4/S3VCgzOuyQI/AAAAAAAAAvw/aww4Ui2N7LU/agile-testing-quadrants.JPG?imgmax=800" target="_blank">le quadrant de tests de Brian Marick</a>.

## Avec TDD, il n&rsquo;y a pas de défaut

Il est clair que TDD doit vous amener vers de la qualité du premier coup. Maintenant, dire que TDD permet d&rsquo;éliminer tous les défauts est faux. Vous aurez toujours des cas non prévus, des problèmes qui peuvent ne pas être testables automatiquement, et il y en a, etc. Maintenant il est clair que votre quantité de défaut (définir ce qu&rsquo;est un défaut mérite un billet de blog à lui-seul) doit baisser. Sinon c&rsquo;est qu&rsquo;il y a un problème dans votre approche.

TDD ne rendra pas non plus votre code parfaitement propre, le parfait n&rsquo;étant qu&rsquo;une affaire de mythologie. En revanche, même sans appliquer des principes de clean code, votre code sera naturellement plus propre qu&rsquo;avant. Evidemment, cela ne suffira pas, et les pratiques de clean code vous amèneront à améliorer le code. Mais sans les tests, c&rsquo;est inenvisageable.

Enfin, TDD vous permettra certainement de maîtriser votre coût du changement (évolution, correction, adaptation&#8230;) et allonger la durée de vie de vos applications. Certes, vous aurez des tests à transformer voire éliminer, mais cela vaut largement les nuits blanches que vous avez l&rsquo;habitude de passer avec votre débugueur.

## Quelques conseils

Pour finir, quelques conseils :

  * Il va falloir désapprendre certaines choses : vous ne pouvez pas progresser en TDD si vous réfléchissez comme vous avez l&rsquo;habitude de le faire. Essayez de vous en affranchir. Et cela demande une certaine humilité : celle de reconnaître qu&rsquo;on ne sait pas vraiment écrire du code qui marche sans tests.
  * Dans vos tests, avancez par petites étapes, les fameuses « tiny steps ». Avancez assertion par assertion. A la limite, vous pouvez utiliser la même méthode pour plusieurs assertions, mais en règle générale, cela va se traduire par une trop grande responsabilité de votre test. Il vaut mieux découper au maximum.
  * Pour commencer, il faut s&rsquo;y mettre de suite, et peut-être lire un bouquin comme « TDD by example » de Kent Beck. Après il faut pratiquer, pratiquer, et encore pratiquer. Vous ne résoudrez pas tous les problèmes d&rsquo;un coup. Ca fait 3 ans que je fais du TDD et je me pose encore pas mal des questions&#8230;
  * J&rsquo;aime nommer mes tests avec un nom parlant. J&rsquo;utilise le style BDD « ShouldDoThisWhenThat&#8230; ». J&rsquo;organise aussi mes tests selon le format « Given/When/Then » qui est très pratique.
  * Enfin, ne passez pas trop de temps à écrire un test. Généralement, c&rsquo;est que vous êtes mal partis. Il se peut aussi que vous tentiez de tester quelque chose et que vous n&rsquo;êtes pas armés pour&#8230; là il vous faut creuser pour trouver le bon outil. D&rsquo;une manière générale, vos tests doivent être FIRST : Fast, Independant, Repeatable, Self-Validating, Timely

Allé sur ce, bon courage !

