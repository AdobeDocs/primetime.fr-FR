---
description: Les demandes d’insertion d’annonces du client spécifient généralement plus d’un débit dans la liste de lecture au format M3U8 de variante. Le serveur de manifeste génère et renvoie un nouveau fichier de variante M3U8 contenant un lien M3U8 distinct pour chaque débit binaire. Il génère également un identifiant de groupe unique pour lier ces M3U8s ensemble.
seo-description: Les demandes d’insertion d’annonces du client spécifient généralement plus d’un débit dans la liste de lecture au format M3U8 de variante. Le serveur de manifeste génère et renvoie un nouveau fichier de variante M3U8 contenant un lien M3U8 distinct pour chaque débit binaire. Il génère également un identifiant de groupe unique pour lier ces M3U8s ensemble.
seo-title: Flux de débit binaire multiples
title: Flux de débit binaire multiples
uuid: f59cb765-e000-43e0-8d3a-8149a3c5b96e
translation-type: tm+mt
source-git-commit: 2c7ac5c1b2d30b7eb819157ee4568739c1bdfb9d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Flux de débit binaire multiples {#multiple-bit-rate-streams}

Les demandes d’insertion d’annonces du client spécifient généralement plus d’un débit dans la liste de lecture au format M3U8 de variante. Le serveur de manifeste génère et renvoie un nouveau fichier de variante M3U8 contenant un lien M3U8 distinct pour chaque débit binaire. Il génère également un identifiant de groupe unique pour lier ces M3U8s ensemble.

Le serveur de manifeste utilise les informations contenues dans la demande d’URL du Bootstrap du client pour récupérer la liste de lecture de la variante de contenu. Il génère une nouvelle liste de lecture variante contenant des liens de serveur manifeste vers le contenu au niveau du flux. Le client les utilise pour créer des requêtes d’insertion publicitaire. Les liens de contenu au niveau du flux du serveur de manifeste présentent le format suivant :

```
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
  {groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **`live/vod`** Le serveur de manifeste définit cette valeur en fonction du type de liste de lecture du contenu : Live/linear (#EXT-X-PLAYLIST-TYPE:ÉVÉNEMENT) ou VOD (#EXT-X-PLAYLIST-TYPE:VOD)

* **`publisherAssetID`** ID unique de l’éditeur pour le contenu spécifique fourni dans la demande d’URL du Bootstrap.

* **`rendition`** Le serveur de manifeste définit cette valeur en fonction de la valeur BANDWIDTH du flux de contenu et l’utilise pour faire correspondre le débit de la publicité au débit de transmission du contenu. Le débit publicitaire ne peut pas dépasser le débit binaire du contenu, sauf si le rendu publicitaire avec le débit binaire le plus faible le fait.

* **`groupID`** Le serveur de manifeste génère cette valeur et l’utilise pour s’assurer qu’il place les publicités de manière cohérente, quel que soit le débit de rendu des publicités demandé par le client.

* **`base64-encoded url of the bit rate stream`** La base64 sécurisée pour l’URL du serveur de manifeste code l’URL absolue du flux de contenu. Chaque flux possède sa propre URL.

* **`Query parameters`** Paramètres de requête fournis dans la demande d’URL du Bootstrap.

