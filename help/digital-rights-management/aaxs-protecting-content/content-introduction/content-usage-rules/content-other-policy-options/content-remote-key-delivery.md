---
seo-title: Diffusion clé iOS locale et distante
title: Diffusion clé iOS locale et distante
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Diffusion clé iOS locale et distante{#remote-and-local-ios-key-delivery}

adobe primetime prend en charge deux options de diffusion clé pour les clients iOS :

* Distant - Exactement comme spécifié dans la spécification HLS, le manifeste M3U8 spécifie un chemin HTTPS qui contient une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque &quot;Remote&quot; est spécifié, le périphérique client se rend sur un serveur HTTPS distant pour récupérer la clé AES.
* Local - Lorsque &quot;Local&quot; est spécifié, au lieu de contacter Internet/réseau pour la clé AES, un serveur HTTPS local est intégré dans l&#39;application iOS qui traitera toutes les requêtes de clés AES. Le serveur HTTPS incorporé est automatiquement configuré et configuré dans l’application Primetime. Aucune intervention n’est requise de la part du développeur d’applications.

La diffusion des clés distantes est activée par le biais de la stratégie utilisée pour compresser le contenu (la modification de ce paramètre nécessite le reconditionnement du contenu). Lorsque la diffusion des clés distantes est activée, un serveur de clés d’accès aux Adobes doit être déployé pour traiter les demandes clés des clients iOS, mais le flux de travail des clients sur d’autres plateformes n’est pas modifié.

>[!NOTE]
>
>La sélection de la diffusion clé n’affecte que les clients iOS. Tous les autres périphériques qui utilisent le contenu HLS utiliseront toujours la diffusion de clé &quot;Local&quot;, même si &quot;Remote&quot; a été spécifié.

Pour plus d’informations, voir *Utilisation du serveur* clé d’accès à l’Adobe.
