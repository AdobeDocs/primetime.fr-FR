---
title: À propos d’Adobe Access Server pour la diffusion en continu protégée
description: À propos d’Adobe Access Server pour la diffusion en continu protégée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# À propos d’Adobe Access Server pour la diffusion en continu protégée{#about-adobe-access-server-for-protected-streaming}

Le serveur Adobe® Access™ pour la diffusion en continu protégée est une mise en oeuvre de serveur de licences basée sur le SDK Adobe Access. Ce serveur émet des licences pour le contenu protégé pour les clients Adobe Access.

Adobe Access Server for Protected Streaming prend en charge plusieurs clients, ce qui signifie qu’un seul serveur peut être hébergé pour plusieurs éditeurs de contenu, chacun disposant de ses propres paramètres de configuration. En outre, le serveur prend en charge les composants d’autorisation personnalisés, de sorte que la logique personnalisée peut être exécutée avant d’émettre une licence.

Ce serveur est destiné à être utilisé avec la diffusion en continu HTTP. Par conséquent, cette mise en oeuvre de serveur ne prend pas en charge toutes les fonctionnalités disponibles dans Adobe Access. Par exemple, Adobe Access Server for Protected Streaming ne prend pas en charge les demandes d’authentification des utilisateurs, les stratégies multiples, les licences liées au domaine, le chaînage de licences ou les messages de synchronisation.
