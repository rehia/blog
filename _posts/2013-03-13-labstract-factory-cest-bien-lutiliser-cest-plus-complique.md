---
id: 388
title: 'L&rsquo;Abstract Factory c&rsquo;est bien, l&rsquo;utiliser, c&rsquo;est plus compliqué'
date: 2013-03-13T10:02:45+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=388
permalink: /labstract-factory-cest-bien-lutiliser-cest-plus-complique/
excerpt_separator: <!--more-->
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
categories:
  - Design
tags:
  - abstract factory
  - architecture
  - design
  - développement
  - factory
---

Je me suis retrouvé récemment face à un problème assez connu. Ce problème consistait à créer, par exemple, différents types d&rsquo;animaux en fonction d&rsquo;un discriminant, comme le type d&rsquo;animal dans notre exemple. La création n&rsquo;étant, dans mon problème, pas triviale, il est assez naturel de faire appel à une Factory pour cela. Mieux ! Une Abstract Factory permet de masquer la complexité de la création de chaque type d&rsquo;animal, en ne laissant à l&rsquo;appelant qu&rsquo;un appel simple du style :

<pre class="brush: csharp; title: C#; notranslate" title="C#">Animal myAnimal = myFactory.CreateAnimal(name, age);</pre>

Simple avez-vous dit ? Pas tout à fait, car « a&rsquo;men donné », comme on dit dans le milieu rugbystique, il va bien falloir instancier « myFactory ». C&rsquo;est là tout l&rsquo;enjeu de ce billet.<!--more-->

## Rappel sur l&rsquo;Abstract Factory

Je dirais même bref rappel. Voilà une image qui résume à elle seule ce qu&rsquo;est une abstract factory :

[<img class="aligncenter size-full wp-image-397" alt="abstract factory" src="{{ site.baseurl }}/wp-content/upload/abstract-factory.png" width="504" height="385" srcset="{{ site.baseurl }}/wp-content/upload/abstract-factory.png 504w, {{ site.baseurl }}/wp-content/upload/abstract-factory-300x229.png 300w" sizes="(max-width: 504px) 100vw, 504px" />]({{ site.baseurl }}/wp-content/upload/abstract-factory.png)

Pour en savoir plus, j&rsquo;ai trouvé ici un meta-lien exceptionnel : <a title="Abstract Factory dans Google" href="http://past.is/d1ZR" target="_blank">http://past.is/d1ZR</a>.

Voilà ! J&rsquo;espère que vous vous êtes rafraîchi la mémoire. Passons à la suite&#8230;

## Consommer l&rsquo;Abstract Factory

Les articles que vous venez peut-être de lire pour vous rafraîchir la mémoire vous ont semblé assez basique. Si vous les relisez, vous remarquerez que l&rsquo;instanciation des factories se fait dans un bon vieux « _main »_ des familles. Entendons-nous bien : l&rsquo;Abstract Factory est une forme d&rsquo;inversion de dépendance. Plutôt que de dépendre de plusieurs factories identiques, qui ont une responsabilité identique (à savoir créer un Animal), on préfère ne dépendre que de leur abstraction.

On cherche donc bien une forme de découplage entre l&rsquo;appelant et les factories en l&rsquo;occurrence. Pour ce qui est des exemples proposés, donc, c&rsquo;est complètement raté, puisque dans l&rsquo;appelant, vous devez connaitre l&rsquo;ensemble des implémentations possibles, et les conditions nécessaires pour utiliser une implémentation ou une autre. Bref, le problème reste entier. A ce stade, je vois au moins deux solutions :

  * <span style="line-height: 13px;">La Factory Method</span>
  * Et la meta-factory

## Factory Method

La première solution qui m&rsquo;a été suggérée c&rsquo;est ni plus ni moins qu&rsquo;une factory method. Cette méthode a pour responsabilité de déterminer quelle implémentation de l&rsquo;abstract factory est la bonne, en fonction de paramètres divers, et d&rsquo;en retourner une instance. Pour plus de « commodité » (mais aussi pour éviter de déborder sur le point suivant et casser mon billet), cette méthode est accessible depuis l&rsquo;abstract factory, et donc de manière statique (puisque la factory est abstraite :). Ce qui revient, dans notre exemple à :

<pre class="brush: csharp; title: C#; notranslate" title="C#">AnimalFactory myFactory = AnimalFactory.GetAnimalFactory(animalType);
Animal myAnimal = myFactory.CreateAnimal(name, age);</pre>

C&rsquo;est parfait n&rsquo;est-ce pas ? Et bien non, en fait&#8230; Moi, ça ne me plait pas du tout. Je vous disais que l&rsquo;abstract factory était là pour nous permettre un découplage. Or l&rsquo;appel statique nous recrée un couplage fort : il n&rsquo;y a aucun moyen de s&rsquo;en défaire, notamment pour rendre le code appelant facilement testable. Finalement on n&rsquo;a fait que déporter le problème&#8230; Voyons donc une autre solution&#8230;

## La meta-factory

La meta factory c&rsquo;est cette idée que puisqu&rsquo;une factory est l&rsquo;artefact idéal à qui déléguer la responsabilité d&rsquo;une création, autant appliquer l&rsquo;idée jusqu&rsquo;au bout, et notamment pour notre abstract factory. La factory d&rsquo;une factory devenant ainsi une meta-factory ! J&rsquo;avoue que l&rsquo;idée même qu&rsquo;un tel type d&rsquo;artefact puisse exister me met en alerte d&rsquo;un risque d&rsquo;overdesign imminent ! Mais soit, si nous allons au bout de l&rsquo;idée, du point de vue de l&rsquo;appelant, cela donne ceci :

<pre class="brush: csharp; title: C#; notranslate" title="C#">MetaAnimalFactory metaFactory = new MetaAnimalFactory(); // qui peut être injecté
AnimalFactory myFactory = metaFactory.GetAnimalFactory(animalType);
Animal myAnimal = myFactory.CreateAnimal(name, age);</pre>

Vu comme ça, cela parait faire un grand nombre de choses à savoir du point de vue de l&rsquo;appelant. Notez quand même que nous ne sommes plus dans le cadre d&rsquo;un appel statique, puisqu&rsquo;un appel statique, c&rsquo;est mal :). Notez aussi que le « new » effectué sur la meta-factory ne vaut pas mieux, sauf qu&rsquo;en l&rsquo;occurrence, on va pouvoir l&rsquo;injecter dans l&rsquo;appelant, en établissant une relation de dépendance entre l&rsquo;appelant et cette meta-factory. Qui plus est, la méthode exposée a un comportement qui s&rsquo;apparente à un transaction script, ce qui nous conforte dans l&rsquo;idée que MetaAnimalFactory peut être injecté dans le constructeur de notre appelant, ceci n&rsquo;étant pas possible avec l&rsquo;abstract factory. Si on fait le bilan, celui-ci n&rsquo;est pas si mauvais. La seule chose qui pose problème c&rsquo;est que le niveau d&rsquo;abstraction n&rsquo;est pas suffisant du point de vue de l&rsquo;appelant, et aussi de savoir que cette factory est une « meta », et n&rsquo;a donc aucun intérêt que celui de fournir la bonne implémentation. Mais ceci peut se corriger facilement, laissant la porte ouverte à une troisième voie&#8230;.

## La troisième voie (donc&#8230;)

L&rsquo;idée de cette idée « ultime », si tant est qu&rsquo;elle le soit, c&rsquo;est de faire croire à l&rsquo;appelant qu&rsquo;il continue de collaborer avec une factory, et de faire en sorte que notre meta-factory agisse comme une factory normale. On va en réalité donner un peu plus de responsabilité à notre fameuse meta factory. Voici le diagramme ajusté :

[<img class="aligncenter size-full wp-image-400" alt="meta factory" src="{{ site.baseurl }}/wp-content/upload/meta-factory1.png" width="500" height="375" srcset="{{ site.baseurl }}/wp-content/upload/meta-factory1.png 500w, {{ site.baseurl }}/wp-content/upload/meta-factory1-300x225.png 300w" sizes="(max-width: 500px) 100vw, 500px" />]({{ site.baseurl }}/wp-content/upload/meta-factory1.png)

Comme vous le voyez, on a fait apparaître une interface, en plus de l&rsquo;abstract factory. L&rsquo;appelant ne collabore plus avec l&rsquo;abstract factory, mais avec cette interface. Autre changement : la meta-factory implémente cette nouvelle interface, agissant ainsi comme une vraie factory. Les implémentations de chaque méthode du contrat consiste donc à déterminer la bonne implémentation à utiliser, et à utiliser l&rsquo;instance créée comme une instance de l&rsquo;abstract factory. Du point de vue de l&rsquo;appelant, cela donne ceci :

<pre class="brush: csharp; title: C#; notranslate" title="C#">IAnimalFactory myFactory // injecté par constructeur
Animal myAnimal = myFactory.CreateAnimal(name, age);</pre>

D&rsquo;un point de vue de l&rsquo;élégance de l&rsquo;API, du découplage, et de la testabilité, on y gagne carrément, puisque l&rsquo;appelant n&rsquo;a même pas connaissance de la fameuse meta factory. Cela peut paraître un peu lourd en terme de nombre d&rsquo;artefacts et de complexité, mais il faut bien imaginer une construction assez complexe justement, pour laquelle une abstract factory se justifie.

## Une meta-quoi ?

J&rsquo;entends d&rsquo;ici les commentaires me disant : « Non, mais Jérôme, tu délires ? Ce dont tu parles ça a un nom et ça s&rsquo;appelle : &#8230; » (avec le lien qui va avec merci !). Et j&rsquo;en ai bien conscience ! Encore une fois cette idée a émergée sur un tableau. Oui, car même en faisant du TDD, on peut aussi lever la tête du guidon régulièrement et se poser quelques questions en posant des concepts sur un tableau. Et malheureusement, je n&rsquo;ai pas trouvé d&rsquo;info sur un pattern existant. Voilà pourquoi d&rsquo;ailleurs je n&rsquo;ai pas envie de lui donner de nom, car je pense évidemment que quelqu&rsquo;un l&rsquo;a fait avant. Donc, vous pouvez m&rsquo;aider en m&rsquo;indiquant des ressources (assez fiables) sur l&rsquo;existence d&rsquo;un pattern de ce type, et je ne manquerai pas d&rsquo;éditer ce post pour les mentionner. J&rsquo;avoue en effet que ce concept de « meta » m&rsquo;est assez désagréable 🙂

N&rsquo;hésitez pas non plus à critiquer cette approche, autant que vous le souhaitez. Je ne prétends pas détenir la vérité. Si vous avez une meilleure idée, partagez-la !

Donc à vos commentaires ! 🙂

