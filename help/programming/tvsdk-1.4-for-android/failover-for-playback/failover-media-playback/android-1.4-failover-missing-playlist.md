---
description: Lorsqu’une sélection complète est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il ne peut pas récupérer, votre application détermine l’étape suivante.
seo-description: Lorsqu’une sélection complète est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il ne peut pas récupérer, votre application détermine l’étape suivante.
seo-title: Basculement de la liste de lecture manquant
title: Basculement de la liste de lecture manquant
uuid: 91a537f3-3e69-4669-8f84-0292c19ac209
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Basculement de la liste de lecture manquant{#missing-playlist-failover}

Lorsqu’une sélection complète est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il ne peut pas récupérer, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution moyenne est manquante, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, il début de télécharger la liste de lecture de variantes et les segments à partir de la position correspondante. Si TVSDK ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, et ainsi de suite. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK va aller au débit supérieur et compter à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité du catalogue. Le événement d&#39;intérêt est le événement `STATE_CHANGED` et le rappel correspondant est la méthode `onStateChanged`. Voici le code qui surveille si le lecteur change son état interne en ERROR :

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

Pour plus d’informations, voir le fichier [!DNL PlayerFragment.java] dans votre SDK :

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
```

Si le réseau côté client est hors service, vous pouvez utiliser ce code pour vérifier.

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

L&#39;API fournit l&#39;URL utilisée pour vérifier si le réseau côté client est hors service. Il doit s’agir d’une URL valide, qui renvoie le code de réponse http 200 sur les requêtes http.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Si setNetworkDownVerificationUrl n’est pas défini, TVSDK utilise par défaut l’url MainManifest pour déterminer si le réseau est hors service.
