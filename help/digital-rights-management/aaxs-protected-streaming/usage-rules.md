---
seo-title: Règles d’utilisation
title: Règles d’utilisation
uuid: 361d07b9-e4c8-47ab-8c45-a1de98c9fed7
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Règles d’utilisation{#usage-rules}

Avec l’Adobe Access Server for Protected Streaming, toutes les règles d’utilisation sont spécifiées sur le serveur via des fichiers de configuration. Toutes les règles d’utilisation spécifiées dans le contenu protégé sont remplacées. Il est donc recommandé d’utiliser une stratégie anonyme simple lors de la création de packs de contenu. Les règles d’utilisation configurables peuvent être définies par client.

L’Adobe Access Server for Protected Streaming prend en charge les règles d’utilisation suivantes :

* Protection Output
* Restrictions des applications Adobe® AIR®, SWF, iOS et Android
* Restrictions de DRM et de module d’exécution
* Application de détection des ruptures de  (sur les plateformes d&#39;accès aux Adobes qui prennent en charge la détection des ruptures de jailleur)
* La mise en cache des licences est désactivée par défaut. La mise en cache de la licence peut être activée en spécifiant la date de fin de la mise en cache ou la durée de mise en cache autorisée (à compter de la délivrance de la licence).
* Plusieurs droits de lecture vous permettent de spécifier différentes combinaisons de protection de sortie, de restrictions d’application et de restrictions DRM/Runtime. Par exemple, il est possible de spécifier différentes exigences de protection de sortie pour chaque plate-forme cliente en utilisant la restriction de module DRM avec la protection de sortie.

>[!NOTE]
>
>Pour prendre en charge la diffusion des clés distantes sur les périphériques iOS, la diffusion des clés distantes doit être activée pour la stratégie utilisée au moment du pack. Ce paramètre ne peut pas être modifié via la configuration du client sur le serveur. ***adobe primetime est nécessaire pour créer des applications iOS capables de lire du contenu protégé par accès à l’Adobe.***

