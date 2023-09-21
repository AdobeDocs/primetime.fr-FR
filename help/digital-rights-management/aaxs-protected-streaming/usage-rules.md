---
title: Règles d’utilisation
description: Règles d’utilisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Règles d’utilisation{#usage-rules}

Avec Adobe Access Server for Protected Streaming, toutes les règles d’utilisation sont spécifiées sur le serveur via des fichiers de configuration. Toutes les règles d’utilisation spécifiées dans le contenu protégé sont remplacées. Il est donc recommandé d’utiliser une stratégie anonyme simple lors du conditionnement du contenu. Les règles d’utilisation configurables peuvent être définies par client.

Adobe Access Server for Protected Streaming prend en charge les règles d’utilisation suivantes :

* Protection de sortie
* Restrictions des applications Adobe® AIR®, SWF, iOS et Android
* Restrictions des modules DRM et d’exécution
* Application de la détection de saut de prison (sur les plateformes d’accès Adobe prenant en charge la détection de saut de prison)
* La mise en cache de licence est désactivée par défaut. La mise en cache de la licence peut être activée en spécifiant la date de fin de la mise en cache ou un temps de mise en cache autorisé (à partir de l’émission de la licence).
* Plusieurs droits de lecture, qui vous permettent de spécifier différentes combinaisons de protection de sortie, de restrictions d’application et de restrictions DRM/Runtime. Par exemple, il est possible de définir différentes exigences de protection de sortie pour chaque plateforme cliente à l’aide de la restriction de module DRM avec protection de sortie.

>[!NOTE]
>
>Pour prendre en charge la diffusion à distance par clé vers les appareils iOS, la diffusion à distance doit être activée pour la stratégie utilisée au moment du conditionnement. Ce paramètre ne peut pas être modifié via la configuration du client sur le serveur. ***Adobe Primetime est nécessaire pour créer des applications iOS capables de lire du contenu protégé par accès Adobe.***
