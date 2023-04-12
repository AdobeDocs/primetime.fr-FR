---
title: Identification des ressources protégées
description: Identification des ressources protégées
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Identification des ressources protégées {#identifying-protected-resources}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Présentation {#overview}

Chaque demande d’autorisation (ou demande d’autorisation) doit contenir un identifiant unique pour la ressource protégée pour laquelle l’utilisateur demande l’accès. Une ressource protégée peut être n’importe quel niveau de contenu autorisé, comme convenu entre un MVPD et les programmeurs participants. Les ressources protégées potentielles doivent s’adapter à cette structure arborescente avec une granularité de plus en plus spécifique :

- Réseau
   - Canal
      - Afficher
         - Épisode
            - Ressource\
                

</br>

## Format RSS du média {#media_rss}

Les ressources peuvent être identifiées par une chaîne simple (un identifiant unique d’un canal) ou peuvent être représentées au format Media RSS (MRSS), comme convenu entre Adobe (ou un partenaire autorisé pour l’authentification Adobe Primetime) et les MVPD et programmeurs participants. La chaîne RSS utilisée comme spécificateur de ressource peut inclure des informations supplémentaires, telles que des évaluations et des métadonnées de contrôle parental.\
 

Si vous utilisez un identifiant de ressource simple, tel que &quot;TNT&quot;, il est supposé représenter un canal et est traduit dans ce spécificateur de ressource RSS :

```RSS
    <rss version="2.0"> 
        <channel>
            <title>TNT</title>
        </channel>
    </rss>
```
 

Un spécificateur plus complexe peut inclure, par exemple, des informations d’évaluation supplémentaires. Vous pouvez transmettre la chaîne RSS entière aux fonctions d’activation d’accès nécessitant un identifiant de ressource, telles que [`getAuthorization()`](/help/authentication/rest-api-reference.md):

```rss
    var resource = 
        '<rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"> 
             <channel>
                 <title>TNT</title>
                 <media:rating scheme="urn:mpaa">pg</media:rating>
             </channel>
         </rss>'; 
    getAuthorization(resource);
```

Les attributs de ressource sont opaques à l’authentification Adobe Primetime ; ils sont simplement transmis au MVPD. Si le MVPD ne reconnaît pas ou ne peut pas analyser votre spécificateur de ressource, il renvoie une erreur à l’authentification Adobe Primetime, qui renvoie l’erreur à votre `tokenRequestFailed()` rappel.

<!--
## Related Information {#related}

-  User Metadata
-  Preflight Authorization
-->