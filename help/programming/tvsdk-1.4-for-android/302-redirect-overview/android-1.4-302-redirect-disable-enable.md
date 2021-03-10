---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.
title: Désactivation ou activation de l’optimisation de la redirection 302
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---


# Optimisation de la redirection HTTP 302 {#http-302-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer la charge de manière plus efficace.

Si une requête de manifeste principale est redirigée et que l’optimisation de la version 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources à partir de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires.

Cette fonction est activée par défaut et vous pouvez modifier ce paramètre.

## Désactivation ou activation de l’optimisation de la redirection 302{#disable-or-enable-redirect-optimization}

Utilisez la propriété `useRedirectedUrl` pour activer la redirection 302 (true) ou la désactiver (false).
Par exemple :

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration as Metadata: 
MetadataNode resourceMetadata = new MetadataNode();  
resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                         networkConfiguration); 
 
//Call MediaResource.createFromURL to set the metadata: 
MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
  
//Load the resource 
mediaPlayer.replaceCurrentItem(resource);
```

