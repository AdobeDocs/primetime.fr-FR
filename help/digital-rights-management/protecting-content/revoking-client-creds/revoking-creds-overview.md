---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Présentation{#overview}

Vous devrez peut-être révoquer les informations d’identification d’un client ou vérifier si un ensemble donné d’informations d’identification a déjà été révoqué sous certaines conditions. Les informations d’identification peuvent être révoquées si elles sont compromises. Lorsque ces problèmes se produisent, les licences ne sont plus délivrées aux clients compromis.

Adobe gère les listes de révocation des certificats (CRL) pour la révocation des clients compromis. Ces listes CRL sont automatiquement appliquées par le SDK. Les serveurs de licences peuvent limiter davantage les clients en interdisant des informations d’identification de machine ou des versions spécifiques de DRM et d’informations d’identification d’exécution. A `RevocationList` peut être créé et transmis dans le SDK pour révoquer les informations d’identification de l’ordinateur. Des versions DRM/runtime spécifiques peuvent être révoquées au niveau de la stratégie DRM en définissant des restrictions de module dans le droit de lecture ou globalement en définissant des restrictions de module dans la variable `HandlerConfiguration`.

La discussion porte sur la révocation des informations d’identification du client.
