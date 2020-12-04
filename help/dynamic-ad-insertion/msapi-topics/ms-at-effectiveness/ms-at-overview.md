---
description: La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybrides.
seo-description: La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybrides.
seo-title: Suivi des publicités
title: Suivi des publicités
uuid: 184b8c36-5e51-42a7-b905-53f2b7b15e49
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Suivi des publicités {#ad-tracking}

La plupart des annonceurs ont besoin d’informations détaillées sur le moment, la durée et le succès de l’affichage de leurs publicités. L’approche la plus efficace consiste à demander au lecteur client d’envoyer des rapports lors de la lecture des publicités, mais le serveur de manifeste prend également en charge le suivi des publicités côté serveur et hybrides.

Lors de l’activation du suivi des publicités, le client spécifie l’une des approches suivantes :

* **** côté clientAvec la liste de lecture hébergée sur une annonce, le serveur envoie au client un fichier JSON, VMAP ou une structure dans un manifeste spécifiant les événements de suivi et les URL. Cette méthode est compatible avec Interactive Advertising Bureau (IAB)

* **** Côté serveur : le client ne participe pas au suivi des publicités. Le serveur envoie toutes les informations de suivi des publicités qu&#39;il peut. Les données de suivi sont calculées uniquement côté serveur et peuvent ne pas correspondre à l’activité de lecture côté client. Par exemple, si un utilisateur final ne vue pas la totalité de la publicité, une fois les segments distribués, le serveur considère toujours la publicité à lire.

* **** HybridIl s’agit du suivi côté client, mais le client envoie ses rapports au serveur de manifeste, qui les transmet aux URL appropriées. Les annonceurs reçoivent les mêmes informations que pour le suivi côté client. Ce mode s&#39;adapte aux clients qui utilisent une connexion Internet restreinte.