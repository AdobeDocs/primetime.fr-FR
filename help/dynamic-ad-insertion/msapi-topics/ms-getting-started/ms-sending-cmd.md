---
description: Utilisez la commande GET HTTP pour interagir avec le serveur de manifeste.
seo-description: Utilisez la commande GET HTTP pour interagir avec le serveur de manifeste.
seo-title: Envoyer une commande au serveur de manifeste
title: Envoyer une commande au serveur de manifeste
uuid: e9680563-d268-406d-87ce-1521a677e9ec
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Envoyer une commande au serveur de manifeste {#send-a-command-to-the-manifest-server}

Utilisez la commande GET HTTP pour interagir avec le serveur de manifeste.

1. Envoyez une demande `HTTP GET` pour une URL d’amorçage construite à l’aide du modèle suivant :

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **** PublisherAssetIDRrequired. ID unique de l’éditeur pour le contenu spécifique.

* **Contenu** URLRrequired. URL du fichier de contenu M3U8, codé Base64 pour être sécurisé dans l&#39;URL du serveur de manifeste. L’URL de contenu doit pointer vers un fichier variante M3U8, même s’il n’y a qu’un seul flux de débit binaire.

* **** Paramètres de requêteCertains sont obligatoires, d&#39;autres facultatifs. Il s&#39;agit de la partie la plus variée de la demande. Ils indiquent au serveur de manifeste quel type de client effectue la demande et ce qu&#39;il souhaite que le serveur de manifeste fasse.

   Par exemple :

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **Requêtes HTTP ou HTTPS**

   Le serveur de manifeste crée des URL à l’aide du même protocole HTTP de la demande du client. Si un lecteur effectue une requête HTTP (http) non sécurisée, le serveur de manifeste renvoie des URL de suivi de manifeste et d’Auditude avec le protocole http. Si un lecteur établit une connexion HTTP sécurisée (https), un serveur manifest, il renvoie des URL de suivi de manifeste et d’Auditude avec le protocole https.

   >[!NOTE]
   >
   >Le serveur de manifeste ne peut pas modifier le protocole (HTTP ou HTTPS) des segments de contenu (.ts) et des balises de suivi tierces. Vous devez contacter le contenu et les fournisseurs d’annonces tiers pour qu’ils configurent les protocoles souhaités.