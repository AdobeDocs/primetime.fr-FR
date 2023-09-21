---
description: L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.
title: Désactivation ou activation de l’optimisation de la redirection 302
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Optimisation des redirections HTTP 302 {#http-302-redirect-optimization}

L’optimisation de la redirection 302 réduit le nombre de 302 réponses de redirection, ce qui permet à votre application d’équilibrer plus efficacement la charge.

Si une requête de manifeste principale est redirigée et que l’optimisation 302 est activée dans votre lecteur, les requêtes suivantes effectuées pour les ressources de ce manifeste utiliseront l’emplacement de domaine final, ce qui évite 302 réponses supplémentaires.

Cette fonction est activée par défaut et vous pouvez la modifier.

## Désactivation ou activation de l’optimisation de la redirection 302{#disable-or-enable-redirect-optimization}

Utilisez la variable `useRedirectedUrl` pour activer la redirection 302 (true) ou la désactiver (false).
Par exemple :

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
