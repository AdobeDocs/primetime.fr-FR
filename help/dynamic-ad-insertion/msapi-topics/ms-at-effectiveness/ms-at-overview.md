---
description: La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybride.
seo-description: La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybride.
seo-title: Suivi des publicités
title: Suivi des publicités
uuid: 184b8c36-5e51-42a7-b905-53f2b7b15e49
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Suivi des publicités {#ad-tracking}

La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybride.

Lors de l’activation du suivi des publicités, le client spécifie l’une des méthodes suivantes :

* **Côté** client En plus de la liste de lecture à assemblage publicitaire, le serveur envoie au client une structure JSON, VMAP ou in-manifest spécifiant les  de suivi et les URL. Cette méthode est conforme à la norme IAB (Interactive Advertising Bureau)

* **Côté** serveur Le client ne participe pas au suivi des publicités. Le serveur envoie toutes les informations de suivi des publicités qu’il peut. Les données de suivi sont calculées uniquement côté serveur et peuvent ne pas correspondre à la lecture côté client  le . Par exemple, si un utilisateur final ne  pas la totalité de la publicité, une fois les segments distribués, le serveur considère toujours la publicité à lire.

* **Hybrid** Il s’agit d’un suivi côté client, mais le client envoie ses rapports au serveur de manifeste, qui les transmet aux URL appropriées. Les annonceurs reçoivent les mêmes informations qu’avec le suivi côté client. Ce mode s’adapte aux clients qui utilisent une connexion Internet restreinte.