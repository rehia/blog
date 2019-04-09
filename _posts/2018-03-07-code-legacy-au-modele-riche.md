---
layout: post
title: Du code legacy à un modèle riche
date: 2018-03-07T20:00:00+02:00
type: conf
description: Ce talk a été donné lors d'un meetup du JUG Lyon. Un talk inspiré par les travaux de refactoring effectué sur une application Java chez Saagie, avec Audrey Neveu. 
public: développeurs, architectes, CTO
video: youtube
youtube-id: RcTM9Rr1VCw
---

La plupart des applications développées le sont en mode CRUD, où toute intention métier est traduite en un enchainement d'opérations sur la base de données, et où le modèle utilisé découle de celui de la base. Pourtant, ces applications cachent très souvent un trésor inestimable : du comportement métier, c'est-à-dire l'ensemble des règles du domaine métier. Et ce trésor passe pourtant au second plan. En faisant un peu d'archéologie, on le retrouve un petit peu partout dans l'UI, dans les services, dans les couches intermédiaires, et même dans la base de données, quand on ne retrouve pas la même règle à plusieurs endroits.

Assurer la cohésion de l'ensemble des comportements du domaine métier est pourtant la clé pour pérenniser les applications. Le Domain Driven Design nous encourage à trouver les bonnes abstractions, et donc les bons modèles en fonction des usages. Mais comment procéder ? Comment refactorer un code finalement très "CRUD", faire émerger un modèle du domaine riche, et le protéger de toute préoccupation technique ? C'est ce que nous verrons lors de cette session de live coding. Jérôme est Software craftsman, fan d'eXtreme Programming, de DDD et de rugby. Mais aussi artisan Héron, touche à tout chez Saagie, et le seul à préférer piocher la data plutôt dans la mer que dans les lacs.
