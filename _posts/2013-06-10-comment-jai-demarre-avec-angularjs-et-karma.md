---
id: 407
title: 'Comment j&rsquo;ai démarré avec AngularJS et Karma&#8230;'
date: 2013-06-10T09:34:31+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=407
permalink: /comment-jai-demarre-avec-angularjs-et-karma/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
image: /wp-content/upload/logo-billet-angular.png
categories:
  - JavaScript
tags:
  - angular
  - angularjs
  - bower
  - grunt
  - gruntjs
  - javascript
  - karma
  - ubuntu
  - webstorm
  - yeoman
  - yo
---

[<img class="size-full wp-image-420 alignleft" alt="logo billet angular" src="http://blog.avoustin.com/wp-content/upload/logo-billet-angular.png" width="326" height="252" srcset="http://blog.avoustin.com/wp-content/upload/logo-billet-angular.png 326w, http://blog.avoustin.com/wp-content/upload/logo-billet-angular-300x231.png 300w" sizes="(max-width: 326px) 100vw, 326px" />](http://blog.avoustin.com/wp-content/upload/logo-billet-angular.png)Depuis quelques semaines, j&rsquo;essaye de réellement sortir de ma zone de confort, et découvrir autre chose que .NET et C#. C&rsquo;est ce que j&rsquo;avais déjà entrepris en fin d&rsquo;année dernière en développant une application que nous avons utilisée pour l&rsquo;Agile Tour Montpellier en Java avec Play Framework. Je pourrai vous faire un retour sur cette expérience un peu plus tard. En attendant, j&rsquo;ai souhaité poursuivre cette ouverture en redécouvrant JavaScript, et essayer d&rsquo;avoir un aperçu de l&rsquo;état de l&rsquo;art de la plateforme.

Et je dois avouer que prendre le train en route n&rsquo;est pas chose aisée. Quel foisonnement ! C&rsquo;est incroyable de voir toutes les initiatives prises pour permettre le développement d&rsquo;applications entières en Javascript, même côté serveur. Il est loin le temps où, peu avant l&rsquo;avènement de frameworks comme jQuery, beaucoup de gens enterraient ce langage que peu de monde ne comprenait et n&rsquo;avait vraiment envie de maîtriser. On peut se rendre compte de cette effervescence par exemple <a title="JSDB.io" href="http://www.jsdb.io/?sort=rating" target="_blank">sur le site JSDB.io</a>, ou encore <a title="InfoQ JS Frameworks" href="http://www.infoq.com/research/top-javascript-mvc-frameworks" target="_blank">à travers cette enquête de InfoQ</a>. Difficile pour un néophyte, ou même quelqu&rsquo;un qui redécouvre, de se faire une idée. En cherchant un peu, je me suis rendu compte que beaucoup de monde disait du bien d&rsquo;AngularJS. J&rsquo;ai donc décidé d&rsquo;y investir du temps, et de monter une plateforme de développement.<!--more-->

Oui j&#8217;emploie le mot plateforme, pour désigner l&rsquo;environnement de développement et les outils ou librairies pour faire du test et de l&rsquo;intégration continue. Difficile pour moi d&rsquo;évaluer quelque chose sans se poser ces questions, puisque écrire un test est la première chose à faire :). Avec AngularJS, votre plateforme peut être assez simple. Si vous n&rsquo;écrivez pas de tests, elle peut même se résumer à un bon vieux Notepad, gedit ou vim. De mon côté, je me suis laissé tenter par l&rsquo;expérience WebStorm, IDE Javascript conçu par l&rsquo;excellent JetBrains, auteur d&rsquo;IntelliJ et ReSharper. Côté librairie de tests, j&rsquo;ai cherché avant tout de quoi avoir un feedback important. J&rsquo;ai donc opté, pour le moment, pour Karma, ex testacular, un runner très intéressant. Enfin, pour les librairies, j&rsquo;hésite encore entre QUnit, Mocha et Jasmine pour les tests unitaires, et entre Jasmine, Angular-scenario et CasperJS pour les tests UI.

En cherchant à mettre en place cette plateforme sous Ubuntu, j&rsquo;ai rencontré quelques difficultés pour traverser la jungle des outils. Je vous propose donc ici un feedback de la mise en place de la plateforme jusqu&rsquo;au premier test vert 🙂

## Préparation

Sous ma version d&rsquo;Ubuntu (12.04), relativement vierge, j&rsquo;ai eu plusieurs outils à installer au préalable, à coup de apt-get : Curl, Git et Nasm.

<pre class="brush: bash; title: bash; notranslate" title="bash">apt-get install nasm
apt-get install curl
apt-get install git
</pre>

Rien d&rsquo;insurmontable. Je vous passe également l&rsquo;installation de WebStorm. <a href="http://www.jetbrains.com/webstorm/webhelp/system-requirements-and-installation.html#d36133e1156" target="_blank">Les détails sont indiqués ici</a>. D&rsquo;ailleurs la plupart d&rsquo;entre vous travaille déjà avec Sublime ou d&rsquo;autres environnements.

## NodeJS et Ruby

La plupart des outils que j&rsquo;ai utilisé ont besoin de Ruby et NodeJS pour s&rsquo;exécuter. Cela ne concerne que les outils, pas nécessairement le code que vous allez écrire. Pour installer ces outils je suis passé par RVM et NVM, ce qui m&rsquo;a été conseillé. Pour NVM, la raison réside surtout dans le fait qu&rsquo;au moment où j&rsquo;ai réalisé ces actions, la suite d&rsquo;outils Yeoman n&rsquo;était pas compatible avec la version 0.10 de NodeJS.

<pre class="brush: bash; title: bash; notranslate" title="bash">\curl -#L https://get.rvm.io | bash -s stable --autolibs=3 --ruby

curl https://raw.github.com/creationix/nvm/master/install.sh | sh
</pre>

Je ne suis pas linuxien pour un sou. Donc pour une raison qui m&rsquo;échappe, NVM n&rsquo;est pas accessible une fois installé. Je n&rsquo;ai pas trouvé d&rsquo;autres moyens que de devoir recharger mon bash\_profile manuellement. Au passage, je vous conseille de copier la ligne correspondant à NVM de votre bash\_profile dans votre bashrc. Si j&rsquo;ai bien compris, c&rsquo;est nécessaire dans le cas d&rsquo;une authentification autre que par le shell (donc typiquement par gnome).

<pre class="brush: bash; title: bash; notranslate" title="bash">. ~/.bash_profile
</pre>

Il reste à installer la bonne version de Node. Comme je le disais, pour ma part j&rsquo;ai dû installer la 0.9 pour faire fonctionner mes outils, alors que la 0.10 était déjà disponible. Vérifiez de votre côté si l&rsquo;upgrade n&rsquo;a pas été fait (notamment pour Yeoman).

<pre class="brush: bash; title: bash; notranslate" title="bash">sudo nvm install 0.9
nvm use 0.9
</pre>

Gardez bien à l&rsquo;esprit la dernière commande, car il vous faudra la réexecuter pour faire fonctionner vos outils à chaque ouverture d&rsquo;un shell.

## Installation de Yeoman, Karma et des templates

La suite consiste à installer l&rsquo;ensemble des outils que l&rsquo;on va utiliser pour développer notre application : Yeoman, Karma et des templates de génération de code.

Yeoman est une suite de 3 outils très pratiques et complémentaires pour aider dans son développement en JS. Yo, le premier outil, est un bootstraper. Il s&rsquo;appuie sur des templates pour bootstraper l&rsquo;application que vous allez développer. Il vous initialise les répertoires, les dépendances, un premier morceau d&rsquo;application, des fichiers de configuration, et tout un tas d&rsquo;autres fichiers comme le robots.txt, le 404.htm ou le .gitignore&#8230; Bref, des choses en moins à se farcir ! Bower est le 2e outil de la suite, réalisé par Twitter. Ce n&rsquo;est ni plus ni moins qu&rsquo;un gestionnaire de packages, spécialisé dans le front-end. Il s&rsquo;appuie sur git et sur un fichier de manifeste pour aller chercher la bonne version du package que vous souhaitez installer. Enfin, le dernier outil, Grunt, est un runner de tâches spécialisé également dans le front-end. En une commande, il peut exécuter toutes les tâches de compilation de coffeescript, de compass, de concaténation et minification de CSS et JavaScript, d&rsquo;exécution des tests, d&rsquo;ouverture d&rsquo;un petit serveur de test, etc. Tout bonnement indispensable !

<pre class="brush: bash; title: bash; notranslate" title="bash">npm install -g yo grunt-cli bower
</pre>

Karma, c&rsquo;est l&rsquo;ancien Testacular, un runner de tests bien pratique pour tester son application sur différents navigateurs. Personnellement, j&rsquo;utilise sa fonction autowatch qui permet d&rsquo;exécuter tous les tests à l&rsquo;enregistrement d&rsquo;un fichier : feedback rapide garanti ! Enfin, les templates de génération sont generator-angular et generator-karma. Avant d&rsquo;installer ces derniers, vous devez créer votre répertoire de projet et aller dedans. A l&rsquo;heure de ces lignes, l&rsquo;installation en mode global par NPM ne fonctionne pas (remplacez my-new-project par ce-que-vous-voulez) :

<pre class="brush: bash; title: bash; notranslate" title="bash">npm install -g karma
mkdir my-new-project && cd $_
npm install generator-angular generator-karma
</pre>

La dernière chose à installer, mais optionnellement, c&rsquo;est Compass. Voilà la ligne de commande :

<pre class="brush: bash; title: bash; notranslate" title="bash">gem update --system
gem install compass
</pre>

## Bootstrap de votre application

Et c&rsquo;est parti pour le bootstrap de votre application ! Vous allez donc lancer la commande yo et suivre le wizard (remontez d&rsquo;un cran si vous êtes dans le répertoire de votre projet) :

<pre class="brush: bash; title: bash; notranslate" title="bash">yo angular my-new-project
</pre>

A vous de suivre ensuite le wizard comme vous l&rsquo;entendez. Personnellement, j&rsquo;ai utilisé Bootstrap et Sass/Compass, pour voir :). Certaines dépendances Angular ne sont pas incluses dans le bootstrap. Il faut donc les installer explicitement si on souhaite les utiliser :

<pre class="brush: bash; title: bash; notranslate" title="bash">bower install angular-cookies
bower install angular-loader
bower install angular-resource
bower install angular-sanitize
</pre>

Il est possible également de rencontrer un bug lors de l&rsquo;utilisation d&rsquo;angular-mocks. On peut, de la même façon, forcer son installation avec bower.

Le projet est maintenant généré ! Il n&rsquo;y a plus qu&rsquo;à l&rsquo;ouvrir dans son IDE. Pour ma part, j&rsquo;ai utilisé WebStorm pour faire tourner une tâche Karma en autowatch. Ainsi, la suite de tests s&rsquo;exécute à l&rsquo;enregistrement d&rsquo;un fichier. Feedback total ! Pour cela, il faut déclarer une tâche de type Node, et la configurer pour faire exécuter la commande :

<pre class="brush: bash; title: bash; notranslate" title="bash">karma start karma.conf.js
</pre>

Il ne faut pas oublier de modifier le fichier de conf karma.conf.js et passer la configuration à autowatch. A ce moment-là de l&rsquo;installation, on a bien avancé ! Il ne reste plus qu&rsquo;à tester l&rsquo;application avec Grunt. Soit avec le paramètre test, pour lancer les tests, soit la commande server, pour tester l&rsquo;application dans un navigateur.

<pre class="brush: bash; title: bash; notranslate" title="bash">grunt test
grunt server
</pre>

Voilà donc pour cette installation ! Comme je le disais, j&rsquo;ai voulu documenter ici tout ce que j&rsquo;ai été amené à faire pour réaliser cette installation. Je ne prétends pas dire que c&rsquo;est la meilleure façon de fonctionner. D&rsquo;ailleurs, à ce sujet, si vous avez des remarques, n&rsquo;hésitez pas à utiliser les commentaires, c&rsquo;est fait pour ! J&rsquo;ai notamment le problème de devoir relancer mon bash_profile à chaque ouverture (ou presque) d&rsquo;un terminal, pour pouvoir réutiliser la commande NVM&#8230; J&rsquo;avoue que c&rsquo;est un peu pénible, et si vous avez une solution, ça m&rsquo;arrangerait !

Bon courage ! Notamment à @vinyll, qui avait pas mal galéré lors de Mix-IT 🙂

