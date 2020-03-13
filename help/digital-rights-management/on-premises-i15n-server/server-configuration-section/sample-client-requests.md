---
seo-title: Exemples de requêtes client
title: Exemples de requêtes client
uuid: 330d5e3c-1711-4375-bd11-e7702f0cde31
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Exemples de requêtes client{#sample-client-requests}

Vous pouvez collecter une bibliothèque d’exemples de requêtes client à l’aide d’outils tels que Charles Proxy ou Wireshark. Vous devez capturer les demandes du client après la configuration du serveur d’individualisation, à l’aide des informations d’identification du transport d’individualisation. Vous pouvez ensuite envoyer ces requêtes client (via *curl* ou un autre outil) au point de terminaison du serveur d’individualisation afin de vérifier que le serveur est opérationnel correctement. Par exemple :

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

Vous pouvez également envoyer à nouveau ces requêtes après toute modification de la configuration du serveur ou mise à jour de ECI/CRL.

Vous devez également mettre à jour correctement la page Statistiques d’individualisation avec les transactions d’individualisation réussies.
