---
title: Présentation
description: Présentation
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Présentation{#overview}

Vous devrez peut-être révoquer les informations d’identification d’un client ou vérifier si un jeu donné d’informations d’identification a déjà été révoqué dans certaines conditions. Les informations d’identification peuvent être révoquées si elles sont compromises. Lorsque ces problèmes se produisent, les licences ne sont plus délivrées à des clients compromis.

Adobe conserve les Listes de révocation des certificats (CRL) pour révoquer les clients compromis. Ces listes CRL sont automatiquement appliquées par le SDK. Les serveurs de licences peuvent restreindre davantage les clients en refusant des informations d’identification d’ordinateur particulières ou des versions particulières des informations d’identification DRM et d’exécution. Un `RevocationList` peut être créé et transmis au SDK pour révoquer les informations d’identification de l’ordinateur. Des versions DRM/runtime particulières peuvent être révoquées au niveau de la stratégie DRM en définissant des restrictions de module dans le droit de lecture ou globalement en définissant des restrictions de module dans le `HandlerConfiguration`.

La discussion porte sur la révocation des informations d’identification du client.
