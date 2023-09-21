---
description: Utilisez la commande de GET HTTP pour interagir avec le serveur de manifeste.
title: Envoi d’une commande au serveur de manifeste
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Envoi d’une commande au serveur de manifeste {#send-a-command-to-the-manifest-server}

Utilisez la commande de GET HTTP pour interagir avec le serveur de manifeste.

1. Envoyer un `HTTP GET` demande d’une URL de bootstrap construite à l’aide du modèle suivant :

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **PublisherAssetID** Obligatoire. Identifiant unique de l’éditeur pour le contenu spécifique.

* **URL de contenu** Obligatoire. URL du fichier de contenu M3U8, codé Base64 pour être sécurisé dans l’URL du serveur de manifeste. L’URL du contenu doit pointer vers un fichier de variante M3U8, même s’il n’y a qu’un flux de débit d’un seul bit.

* **Paramètres de requête** Certains sont obligatoires, d’autres facultatifs. Il s’agit de la partie la plus variée de la requête. Ils indiquent au serveur de manifeste quel type de client effectue la demande et ce qu’il souhaite que le serveur de manifeste fasse.

  Par exemple :

  ```
  https://manifest.auditude.com/auditude/variant/
   {publisherAssetID}/{Content URL (base64)}.m3u8?
  u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
  &pttrackingversion=v2&live=false
  ```

  **Requêtes HTTP/HTTPS**

  Le serveur de manifeste crée des URL à l’aide du même protocole HTTP que la requête du client. Si un lecteur effectue une requête HTTP (http) non sécurisée, le serveur de manifeste renvoie des URL de manifeste et des URL de suivi Auditude avec le protocole http. Si un lecteur établit une connexion HTTP (https) sécurisée, un serveur de manifeste, il renvoie les URL de manifeste et les URL de suivi Auditude avec le protocole https.

  >[!NOTE]
  >
  >Le serveur de manifeste ne peut pas modifier le protocole (HTTP ou HTTPS) des segments de contenu (.ts) et des balises de suivi tierces. Vous devez contacter le contenu et les fournisseurs d’annonces tiers pour qu’ils configurent les protocoles souhaités.