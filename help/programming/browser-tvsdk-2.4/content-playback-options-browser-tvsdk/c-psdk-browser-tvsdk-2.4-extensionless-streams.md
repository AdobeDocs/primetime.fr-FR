---
description: Le navigateur TVSDK prend actuellement en charge la lecture de diffusions dans lesquelles les manifestes et les fragments ne contiennent pas d’extensions.
title: Flux sans extension
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Flux sans extension{#extensionless-streams}

Le navigateur TVSDK prend actuellement en charge la lecture de diffusions dans lesquelles les manifestes et les fragments ne contiennent pas d’extensions.

## Niveau de fragment {#section_0E035129501D4A77BBC14192D8A53A86}

Le navigateur TVSDK analyse les premiers octets de la réponse pour détecter le type de contenu des fragments sans extension. Si aucun type de contenu valide n’est détecté, le navigateur TVSDK renvoie une erreur.

## Niveau de manifeste {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Le navigateur TVSDK utilise la variable `mediaResource.resourceType` qui est transmis dans la variable `replaceCurrentResource` pour détecter le type de contenu de l’URL manifeste. Pour plus d’informations, voir `AdobePSDK.MediaPlayer` classe .

Dans le lecteur de structure de l’interface utilisateur, vous pouvez spécifier le type de ressource dans la ressource multimédia comme suit :

```js
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
  player: { 
    mediaResource: { 
      resourceUrl:'Specify Resource Url', 
      resourceType: ‘Specify Resource Type. Refer AdobePSDK.MediaResourceType' 
    } 
  } 
}); 
```

If `resourceType` n’est pas fourni, l’IU Framework détermine le type de ressource à partir de l’extension URL de ressource, qui est ensuite transmis à `replaceCurrentResource` .

>[!TIP]
>
>Pour un manifeste sans extension, assurez-vous que `resourceType` est toujours transmis lors du chargement d’une ressource dans l’interface utilisateur.
