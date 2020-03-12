---
description: Si pttrackingmode=simple ou ptplayer=ios-mobileweb, le serveur de manifeste renvoie un fichier au format JSON contenant Master-M3U8, URL que le client doit utiliser pour demander le fichier M3U8 décrivant le contenu.
seo-description: Si pttrackingmode=simple ou ptplayer=ios-mobileweb, le serveur de manifeste renvoie un fichier au format JSON contenant Master-M3U8, URL que le client doit utiliser pour demander le fichier M3U8 décrivant le contenu.
seo-title: Format JSON pour l’URL de demande de liste de lecture du manifeste de variante
title: Format JSON pour l’URL de demande de liste de lecture du manifeste de variante
uuid: 9f9693d0-3c93-4555-b20c-7f4576742f41
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Format JSON pour l’URL de demande de liste de lecture du manifeste de variante {#json-format-for-url-for-requesting-variant-manifest-playlist}

Si `pttrackingmode=simple` ou `ptplayer=ios-mobileweb`, le serveur de manifeste renvoie un fichier au format JSON contenant Master-M3U8, URL à utiliser par le client pour demander le fichier M3U8 décrivant le contenu.

Il s’agit du format du fichier JSON contenant l’ `Master-M3U8` URL.

```
{
"Master-M3U8": "https://manifest.auditude.com/auditude/variant/{publisherAssetID}/
  {sessionId}/{Base 64 of the url of the content}.m3u8
  ?u={Ad Request Id}
  &z={Ad Zone Id}
  &pttrackingmode=simple
  &pttrackingversion=v1
  &{other query parameters}"
}
```
