---
description: Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.
seo-description: Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.
seo-title: Flux sans extensibilité
title: Flux sans extensibilité
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Flux sans extensibilité {#extensionless-streams}

Le navigateur TVSDK prend actuellement en charge la lecture de flux dans lesquels les manifestes et les fragments ne contiennent pas d’extensions.

## Niveau de fragment {#section_0E035129501D4A77BBC14192D8A53A86}

Le navigateur TVSDK analyse les premiers octets de la réponse pour détecter le type de contenu des fragments sans extension. Si aucun type de contenu valide n’est détecté, le navigateur TVSDK renvoie une erreur.

## Niveau de manifeste {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

Le navigateur TVSDK utilise le paramètre `mediaResource.resourceType` transmis dans la méthode `replaceCurrentResource` pour détecter le type de contenu de l’URL manifeste. Pour plus d&#39;informations, consultez la classe `AdobePSDK.MediaPlayer`.

Dans le lecteur UI Framework, vous pouvez spécifier le type de ressource dans la ressource média comme suit :

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

Si `resourceType` n&#39;est pas fourni, le cadre d&#39;interface utilisateur détermine le type de ressource à partir de l&#39;extension URL de ressource, qui est ensuite transmis à la méthode `replaceCurrentResource`.

>[!TIP]
>
>Pour un manifeste sans extension, veillez à ce que `resourceType` soit toujours transmis lors du chargement d&#39;une ressource dans l&#39;interface utilisateur.

