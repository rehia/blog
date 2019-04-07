---
id: 15
title: Générer un PostBack en ASP.NET
date: 2011-01-24T22:34:33+02:00
author: Jérôme
layout: post
guid: http://blog.avoustin.com/?p=15
permalink: /generer-un-postback-en-asp-net/
categories:
  - ASP.NET
tags:
  - ASP.NET
  - ClientScriptManager
  - GetPostbackEventReference
  - handler
  - IPostBackEventHandler
  - jQuery
  - postback
  - PostBackOptions
  - RaisePostBackEvent
  - usercontrol
---

C&rsquo;est la première fois en ASP.NET que je me retrouve confronté au problème suivant : Quel code javascript générer pour effectuer un postback vers le serveur sur une action quelconque ?

Tout est parti d&rsquo;une action de maintenance qui a consisté à remplacer le vieillo prototype et sa « lightbox » par le très populaire jQuery et son « dialog ».<!--more--> Ces deux frameworks javascript disposent en effet chacun d&rsquo;un composant de boite de dialogue. Pour limiter l&rsquo;adhérence à l&rsquo;une des technologies, j&rsquo;ai donc « masqué » le composant dialog dans un 

_UserControl_.

## Déclarer un événement

Le clic sur l&rsquo;un des deux boutons de mon _UserControl_ génère un événement auquel la page dans laquelle il se situe peut s&rsquo;abonner. Pour rappel, il faut déclarer un événement dans le _UserControl_ de cette façon :

<pre class="brush: csharp; title: C#; notranslate" title="C#">public event EventHandler ButtonLeftClick;</pre>

Notez qu&rsquo;il n&rsquo;est pas indispensable de déclarer votre propre _delegate_. Vous pouvez tout à fait utiliser _EventHandler_, si vous n&rsquo;avez pas de données particulières à transmettre au handler de l&rsquo;événement. Jusque là, rien de très exotique !

Maintenant, comment propager mon événement ? Comment le rattacher au clic du bouton de ma boîte de dialogue ? Tous les exemples trouvés sur le net montrent à quel point il est facile de le faire : il suffit de créer un handler dans le _UserControl_ qui est associé à l&rsquo;événement _OnClick_ du bouton ASP.NET&#8230; Oui, mais voilà : un dialog jQuery est composé de boutons&#8230; jQuery !

## Générer le PostBack

Nous voilà donc arrivé à notre question initiale : Comment générer un postback depuis la page web, sur le clic de mon bouton ?

L&rsquo;**une** des solutions se trouve dans la classe **ClientScriptManager**, qui dispose, entre autres, de la méthode **_GetPostbackEventReference_**. Cette méthode, qui possède 4 surcharges, permet en effet de générer le code javascript qui va effectuer le postback. Il existe un certain nombre d&rsquo;options permettant de paramétrer le postback. Il est notamment possible de définir :

  * l&rsquo;url du postback avec _ActionUrl_, si cette url est différente de la page actuelle du navigateur;
  * si le postback est précédé de la validation du formulaire, avec _PerformValidation_, et le groupe de validation auquel le contrôle appartient, avec _ValidationGroup_;
  * l&rsquo;activation de l&rsquo;_AutoPostBack_, notamment pour les listes déroulantes, cases à cocher, radio boutons, etc.

Enfin, trois derniers paramètres, et non des moindres :

  * _Argument_, pour spécifier un argument quelconque,
  * _TargetControl_, qui est le UserControl lui-même, dans notre exemple.
  * et _ClientSubmit_, qu&rsquo;il faut passer à true, pour permettre la génération du code javascript de postback.

Voici donc un exemple de code à insérer :

<pre class="brush: csharp; title: C#; notranslate" title="C#">Page.ClientScript.GetPostBackEventReference(
    new PostBackOptions(this, this.ClientID, Request.RawUrl,
        false, true, false, true, false, string.Empty));</pre>

Et voici le code généré par ASP.NET dans le rendu HTML :

<pre class="brush: xml; title: HTML; notranslate" title="HTML">&lt;input type="button" id="btnTest" value="Cliquer ici pour tester"
    onclick='javascript:WebForm_DoPostBackWithOptions(
        new WebForm_PostBackOptions("ctl00$MainContent$uc2",
            "MainContent_uc2", false, "", "/Default.aspx", false, true))' /&gt;</pre>

Il en existe évidemment d&rsquo;autres, mais je vous renvoie pour cela à la <a title="Référence MSDN pour GetPostBackEventReference" href="http://msdn.microsoft.com/fr-fr/library/ms153109.aspx" target="_blank">documentation officielle dans le MSDN</a>. Attention toutefois lors de l&rsquo;utilisation de la méthode _GetPostbackEventReference_ !

Première chose : si vous intégrez le javascript généré dans un code javascript plus large, il vous faut ajouter un « ; » en fin de script. La méthode ne génère en effet pas ce point-virgule, puisque ce code est utilisé la majorité du temps directement dans un événement onclick, onblur, onchange, etc.

Deuxième chose : dans notre exemple, il faut penser que le _UserControl_ peut être ajouté plusieurs fois dans une page. Et si vous faites ce test, vous verrez qu&rsquo;il ne suffit pas d&rsquo;attacher un handler à l&rsquo;événement du côté de la page, et détecter si un handler est attaché côté _UserControl_. En effet, vous aurez la drôle de surprise de voir que seul le handler du dernier user control déclaré dans la page est appelé ! Pour contourner cela, il est nécessaire de définir une valeur à l&rsquo;option _Argument_. Et autant que possible il faut spécifier une valeur **unique** pour éviter là encore des surprises. La meilleure solution consiste à y renseigner le _ClientID_ ou le _UniqueID_ du _UserControl_.

## Déclencher l&rsquo;appel au handler

Dernière question qui peut se poser : à quel moment « détecter » qu&rsquo;un postback concernant le _UserControl_ a été réalisé, et comment déterminer s&rsquo;il correspond bien à l&rsquo;instance du _UserControl_ (et pas à une autre) ?

Pour cela, il existe en ASP.NET deux interfaces : _**IPostBackEventHandler**_ et _**IPostBackDataHandler**_. Le _UserControl_ doit impélmenter l&rsquo;une des deux interfaces. La première sert simplement à détecter qu&rsquo;un événement a été levé. La deuxième sert en plus à vérifier si le _UserControl_ a changé ou non d&rsquo;état. Dans notre exemple, c&rsquo;est la première interface, très simple d&rsquo;usage, qui va nous intéresser.

L&rsquo;interface _IPostBackEventHandler_ dispose de la seule méthode _**RaisePostBackEvent**_.

<pre class="brush: csharp; title: C#; notranslate" title="C#">void RaisePostBackEvent(string eventArgument);</pre>

Vous noterez que lorsqu&rsquo;ASP.NET appelle cette méthode, il passe directement l&rsquo;argument lié à l&rsquo;événement. Cela tombe à point nommé puisque nous avons auparavant défini cet argument. Il suffit alors simplement de vérifier que l&rsquo;argument correspond bien à celui de l&rsquo;instance (d&rsquo;où l&rsquo;utilisation d&rsquo;une valeur unique) pour déclencher l&rsquo;appel au handler de la page.

<pre class="brush: csharp; title: C#; notranslate" title="C#">public void RaisePostBackEvent(string eventArgument)
{
    if (eventArgument == this.ClientID & ButtonClick != null)
        ButtonClick(this, EventArgs.Empty);
}</pre>

## Le fonctionnement événementiel totalement assumé

Lors de sa sortie, ASP.NET s&rsquo;est clairement affiché comme une plateforme web de gestion d&rsquo;événements. Il est parfois difficile de s&rsquo;y retrouver et de faire les bons choix lorsque l&rsquo;on ne maîtrise pas totalement le cycle de vie.

Cependant, la plateforme a su évoluer pour donner aux équipes les moyens de progresser et de simplifier grandement leurs développements&#8230; Encore faut-il être conscient des outils que l&rsquo;on a à sa disposition !

