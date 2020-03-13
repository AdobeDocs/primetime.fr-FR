---
seo-title: Révocation des informations d’identification du client
title: Révocation des informations d’identification du client
uuid: 47f1ec1a-bd8f-4f8c-bee3-bfbf6d9902e7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Révocation des informations d’identification du client{#revoking-client-credentials}

Dans certaines conditions, il est nécessaire de révoquer les informations d’identification d’un client ou de vérifier si un jeu donné d’informations d’identification a déjà été révoqué. Les informations d’identification peuvent être révoquées si elles sont compromises. Dans ce cas, les licences ne seront plus délivrées aux clients compromis.

Adobe conserve les  de révocation des certificats (CRL) pour révoquer des clients compromis. Ces listes CRL sont automatiquement appliquées par le SDK. Les serveurs de licences peuvent limiter davantage les clients en refusant des informations d’identification d’ordinateur particulières ou des versions particulières des informations d’identification DRM et d’exécution. Il `RevocationList` est possible de créer et de transmettre un fichier SDK pour révoquer les informations d’identification de l’ordinateur. Des versions DRM/runtime spécifiques peuvent être révoquées au niveau de la stratégie (en définissant des restrictions de module dans la droite de lecture) ou globalement (en définissant des restrictions de module dans la `HandlerConfiguration`).

La discussion de ce chapitre porte sur la révocation des informations d’identification des clients.
