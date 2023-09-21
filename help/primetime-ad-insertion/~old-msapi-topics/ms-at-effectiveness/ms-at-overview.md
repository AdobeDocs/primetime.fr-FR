---
description: La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur manifeste prend également en charge le suivi des publicités côté serveur et hybride.
title: Suivi des publicités
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Suivi des publicités {#ad-tracking}

La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur manifeste prend également en charge le suivi des publicités côté serveur et hybride.

Lors de l’activation du suivi des publicités, le client applique l’une des méthodes suivantes :

* **Côté client** Avec la liste de lecture assemblée par les publicités, le serveur envoie au client une structure JSON, VMAP ou in-manifest spécifiant les événements de suivi et les URL. Cette méthode est conforme à l’IAB (Interactive Advertising Bureau)

* **Côté serveur** Le client ne participe pas au suivi des publicités. Le serveur envoie toutes les informations de suivi des publicités qu’il peut. Les données de suivi sont calculées uniquement côté serveur et peuvent ne pas correspondre à l’activité de lecture côté client. Par exemple, si un utilisateur final ne consulte pas l’intégralité de la publicité, une fois les segments distribués, le serveur considère toujours la publicité à lire.

* **Hybride** Il s’agit d’un suivi côté client, mais le client envoie ses rapports au serveur manifeste, qui les transmet aux URL appropriées. Les annonceurs reçoivent les mêmes informations que pour le suivi côté client. Ce mode prend en charge les clients utilisant un accès Internet restreint.