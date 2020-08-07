---
description: Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec des fichiers de configuration.
seo-description: Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec des fichiers de configuration.
seo-title: A propos des règles d’utilisation
title: A propos des règles d’utilisation
uuid: 4a794712-db58-43f5-b867-8871e58e12ae
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# A propos des règles d’utilisation{#about-usage-rules}

Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec des fichiers de configuration.

Toutes les règles d’utilisation spécifiées dans la stratégie DRM pour le contenu protégé sont remplacées. Par conséquent, l’Adobe vous recommande d’utiliser une stratégie DRM simple et anonyme lors de la création d’un pack de contenu. Toutes les règles d’utilisation que vous pouvez configurer peuvent être configurées par client.

Le serveur DRM Primetime pour la diffusion en flux continu protégée prend en charge les règles d’utilisation suivantes :

* Protection Output
* Restrictions des applications Adobe® AIR®, SWF, iOS et Android
* Restrictions de DRM et de module d’exécution
* Application de détection de rupture de prison sur les plates-formes DRM Primetime prenant en charge la détection de rupture de prison
* La mise en cache des licences est désactivée par défaut. Mise en cache des licences que vous pouvez activer en spécifiant la date de fin de mise en cache ou la durée de mise en cache autorisée ; elle début lorsque la licence est délivrée.
* Plusieurs droits de lecture vous permettent de spécifier différentes combinaisons de protection de sortie, de restrictions d’application et de restrictions DRM/Runtime. Par exemple, vous pouvez spécifier différentes exigences de protection de sortie pour chaque plate-forme cliente en utilisant la restriction de module DRM avec la protection de sortie.

>[!NOTE]
>
>Si vous souhaitez prendre en charge la diffusion des clés distantes sur les périphériques iOS, la diffusion des clés distantes doit être activée pour la stratégie DRM appliquée au moment du pack. Ce paramètre ne peut pas être modifié via la configuration du client sur le serveur.

