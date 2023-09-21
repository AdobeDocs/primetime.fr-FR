---
title: Diffusion clé iOS locale et distante
description: Diffusion clé iOS locale et distante
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Diffusion clé iOS locale et distante{#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge deux options de remise clé aux clients iOS :

* Remote : exactement comme spécifié dans la spécification HLS, le manifeste M3U8 spécifie un chemin HTTPS qui contient une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque &quot;Remote&quot; est spécifié, le périphérique client accède à un serveur HTTPS distant pour récupérer la clé AES.
* Local : lorsque &quot;Local&quot; est spécifié, au lieu de contacter Internet/réseau pour la clé AES, un serveur HTTPS local est incorporé dans l’application iOS qui traitera toutes les requêtes de clé AES. Le serveur HTTPS incorporé est automatiquement configuré et configuré dans l’application Primetime. Aucune intervention n’est requise par le développeur de l’application.

La diffusion par clé distante est activée par le biais de la stratégie utilisée pour empaqueter le contenu (la modification de ce paramètre nécessite un reconditionnement du contenu). Lorsque la diffusion par clé distante est activée, un serveur de clé d’accès par Adobe doit être déployé pour traiter les demandes clés des clients iOS, mais le processus ne change pas pour les clients d’autres plateformes.

>[!NOTE]
>
>La sélection de diffusion Clé n’affecte que les clients iOS. Tous les autres appareils qui utilisent du contenu HLS utiliseront toujours la diffusion clé &quot;locale&quot;, même si &quot;à distance&quot; a été spécifié.

Pour plus d’informations, voir *Utilisation du serveur de clé d’accès Adobe*.
