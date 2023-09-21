---
description: Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation sur le serveur avec les fichiers de configuration.
title: À propos des règles d’utilisation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# À propos des règles d’utilisation{#about-usage-rules}

Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation sur le serveur avec les fichiers de configuration.

Toutes les règles d’utilisation spécifiées dans la stratégie DRM pour le contenu protégé sont remplacées. Par conséquent, Adobe vous recommande d’utiliser une stratégie DRM simple et anonyme lors du conditionnement du contenu. Toutes les règles d’utilisation que vous pouvez configurer peuvent être configurées par client.

Le serveur DRM Primetime pour la diffusion protégée prend en charge les règles d’utilisation suivantes :

* Protection de sortie
* Restrictions des applications Adobe® AIR®, SWF, iOS et Android
* Restrictions des modules DRM et d’exécution
* Application de la détection de saut de prison sur les plateformes DRM Primetime prenant en charge la détection de saut de prison
* La mise en cache de licence est désactivée par défaut. Mise en cache de la licence que vous pouvez activer en spécifiant la date de fin de la mise en cache ou une durée de mise en cache autorisée ; elle commence lorsque la licence est émise.
* Plusieurs droits de lecture qui vous permettent de spécifier différentes combinaisons de protection de sortie, de restrictions d’application et de restrictions DRM/Runtime. Par exemple, vous pouvez définir différentes exigences de protection de sortie pour chaque plateforme cliente à l’aide de la restriction de module DRM avec protection de sortie.

>[!NOTE]
>
>Si vous souhaitez prendre en charge la diffusion de clé distante vers les appareils iOS, la stratégie DRM appliquée au moment du conditionnement doit avoir activé la diffusion de clé distante. Ce paramètre ne peut pas être modifié via la configuration du client sur le serveur.
