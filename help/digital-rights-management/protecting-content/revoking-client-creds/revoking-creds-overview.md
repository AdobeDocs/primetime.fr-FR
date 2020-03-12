---
seo-title: Présentation
title: Présentation
uuid: c6f54867-d0a3-43fd-9493-6496f1b7831a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation{#overview}

Vous devrez peut-être révoquer les informations d’identification d’un client ou vérifier si un jeu donné d’informations d’identification a déjà été révoqué dans certaines conditions. Les informations d’identification peuvent être révoquées si elles sont compromises. Lorsque ces problèmes se produisent, les licences ne sont plus délivrées aux clients compromis.

Adobe conserve les  de révocation des certificats (CRL) pour révoquer des clients compromis. Ces listes CRL sont automatiquement appliquées par le SDK. Les serveurs de licences peuvent limiter davantage les clients en refusant des informations d’identification d’ordinateur particulières ou des versions particulières des informations d’identification DRM et d’exécution. Il `RevocationList` est possible de créer et de transmettre un fichier SDK pour révoquer les informations d’identification de l’ordinateur. Des versions DRM/runtime spécifiques peuvent être révoquées au niveau de la stratégie DRM en définissant des restrictions de module dans le droit de lecture ou globalement en définissant des restrictions de module dans le `HandlerConfiguration`.

La discussion porte sur la révocation des informations d’identification du client.
