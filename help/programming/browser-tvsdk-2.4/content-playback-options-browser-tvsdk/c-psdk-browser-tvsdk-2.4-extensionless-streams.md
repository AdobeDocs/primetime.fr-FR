---
description: Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.
seo-description: Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.
seo-title: Flux sans extensibilité
title: Flux sans extensibilité
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Flux sans extensibilité{#extensionless-streams}

Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.

## Niveau de fragment {#section_0E035129501D4A77BBC14192D8A53A86}

Le navigateur TVSDK analyse les premiers octets de la réponse pour détecter le type de contenu des fragments sans extension. Si aucun type de contenu valide n’est détecté, le navigateur TVSDK renvoie une erreur.

## Niveau de manifeste {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Le navigateur TVSDK utilise le `mediaResource.resourceType` paramètre transmis dans la `replaceCurrentResource` méthode pour détecter le type de contenu de l’URL manifeste. Pour plus d’informations, voir la `AdobePSDK.MediaPlayer` classe.

Dans le lecteur UI Framework, vous pouvez spécifier le type de ressource dans la ressource multimédia comme suit :

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

S’ `resourceType` il n’est pas fourni, la structure de l’interface utilisateur détermine le type de ressource à partir de l’extension d’URL de ressource, qui est ensuite transmise à `replaceCurrentResource` la méthode.

>[!TIP]
>
>Pour un manifeste sans extension, veillez à ce que `resourceType` soit toujours transmis lors du chargement d’une ressource dans l’interface utilisateur.

