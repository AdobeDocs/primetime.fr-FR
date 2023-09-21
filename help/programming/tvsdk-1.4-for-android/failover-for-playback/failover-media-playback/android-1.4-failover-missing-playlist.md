---
description: Lorsqu’une liste de lecture entière est manquante, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur ne se télécharge pas, TVSDK tente de récupérer. S’il ne peut pas récupérer, votre application détermine l’étape suivante.
title: Basculement de la liste de lecture manquant
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Basculement de la liste de lecture manquant{#missing-playlist-failover}

Lorsqu’une liste de lecture entière est manquante, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur ne se télécharge pas, TVSDK tente de récupérer. S’il ne peut pas récupérer, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est manquante, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, il commence à télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si TVSDK ne trouve pas la même liste de lecture de résolution, il tentera de parcourir d’autres listes de lecture à débit binaire et leurs variantes. Un débit inférieur immédiat est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK accède au débit supérieur et compte à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité de catalogue. L’événement ciblé est le suivant : `STATE_CHANGED` et le rappel correspondant est `onStateChanged` . Voici le code qui surveille si le lecteur change son état interne en ERROR :

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

Pour plus d’informations, voir [!DNL PlayerFragment.java] dans votre SDK :

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
```

Si le réseau côté client est hors service, vous pouvez utiliser ce code pour vérifier.

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

L’API fournit l’URL utilisée pour vérifier si le réseau côté client est hors service. Il doit s’agir d’une URL valide, qui renvoie le code de réponse http 200 sur les requêtes http.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Si setNetworkDownVerificationUrl n’est pas défini, TVSDK utilise l’URL MainManifest par défaut pour déterminer si le réseau est hors service.
