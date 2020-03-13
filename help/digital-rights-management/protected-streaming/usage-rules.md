---
description: Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec les fichiers de configuration.
seo-description: Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec les fichiers de configuration.
seo-title: A propos des règles d’utilisation
title: A propos des règles d’utilisation
uuid: 4a794712-db58-43f5-b867-8871e58e12ae
translation-type: tm+mt
source-git-commit: 68f1318db89cf9422f5969f669c11f3784560db6

---


# A propos des règles d’utilisation{#about-usage-rules}

Avec Adobe Primetime DRM Server for Protected Streaming, vous pouvez spécifier toutes les règles d’utilisation du serveur avec les fichiers de configuration.

Toutes les règles d’utilisation spécifiées dans la stratégie DRM pour le contenu protégé sont remplacées. Par conséquent, Adobe vous recommande d’utiliser une stratégie DRM simple et anonyme lors de la création de packages de contenu. Toutes les règles d’utilisation que vous pouvez configurer peuvent être configurées par client.

Le serveur DRM Primetime pour la diffusion en flux continu protégée prend en charge les règles d’utilisation suivantes :

* Protection Output
* Restrictions des applications Adobe® AIR®, SWF, iOS et Android
* Restrictions relatives aux modules DRM et d’exécution
* Application de la détection des violations de sécurité sur les plates-formes DRM Primetime prenant en charge la détection des violations de sécurité
* La mise en cache des licences est désactivée par défaut. Mise en cache des licences que vous pouvez activer en spécifiant la date de fin de mise en cache ou une durée de mise en cache autorisée ; elle est lors de la délivrance de la licence.
* Plusieurs droits de lecture vous permettent de spécifier différentes combinaisons de protection de sortie, de restrictions d’application et de restrictions DRM/Runtime. Par exemple, vous pouvez spécifier différentes exigences de protection de sortie pour chaque plate-forme client en utilisant la restriction du module DRM avec la protection de sortie.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si vous souhaitez prendre en charge le de clés distantes sur les périphériques iOS, la stratégie DRM appliquée au moment de la création du pack doit avoir pour  l’de clés distantes activé. Ce paramètre ne peut pas être modifié via la configuration du client sur le serveur.

