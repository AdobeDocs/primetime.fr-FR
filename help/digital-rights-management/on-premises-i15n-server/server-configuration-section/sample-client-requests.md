---
title: Exemples de requêtes client
description: Exemples de requêtes client
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# Exemples de requêtes client{#sample-client-requests}

Vous pouvez collecter une bibliothèque d’exemples de requêtes client à l’aide d’outils tels que Charles Proxy ou Wireshark. Vous devez capturer les requêtes du client après la configuration du serveur d’individualisation, à l’aide des informations d’identification du transport d’individualisation. Vous pouvez ensuite envoyer ces requêtes client (via *curl* ou un autre outil) au point de terminaison du serveur d’individualisation afin de vérifier que le serveur est correctement opérationnel. Par exemple :

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

Vous pouvez également envoyer à nouveau ces requêtes après toute modification de la configuration du serveur ou mise à jour de ECI/CRL.

Vous devez également mettre à jour la page Statistiques d’individualisation de manière appropriée avec les transactions d’individualisation réussies.
