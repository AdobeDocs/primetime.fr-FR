---
description: Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.
seo-description: Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.
seo-title: Lecture et basculement du média
title: Lecture et basculement du média
uuid: 197a6ee0-f1ff-40ac-bd49-eafeae6167d4
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lecture et basculement du média{#media-playback-and-failover}

Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_E6B6A15930894F56A0A8501577B35E7F}

Lorsqu’une liste de lecture entière est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il est impossible de le récupérer, l’application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est absente, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, il  télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si TVSDK ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK ira au débit supérieur et compte en bas à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Vous pouvez, par exemple, fermer le lecteur  le  du et diriger l’utilisateur vers le de  de de catalogue. Le  d’intérêt est le `STATUS_CHANGED` , et le rappel correspondant est la `onStatusChange` méthode. Le code suivant contrôle si le lecteur change son état interne en ERROR :

Pour plus d’informations, voir le `PSDKDemo` fichier. Les écouteurs de  sont associés à l’instance MediaPlayer.

```
case MediaPlayerStatus.ERROR: 
Alert.show(event.error.toString(), “Error occurred”); 
break;
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

Si setNetworkDownVerificationUrl n’est pas défini, TVSDK utilise l’URL MainManifest par défaut pour déterminer si le réseau est hors service.

## Basculement de segment manquant {#section_ED8CF666289042D39E9914D42BDD9BA4}

Lorsqu’un segment est manquant, par exemple lorsqu’un segment particulier ne parvient pas à être téléchargé, TVSDK tente de récupérer par le biais de diverses tentatives de basculement. S’il ne parvient pas à récupérer, une erreur est générée.

Si un segment est manquant sur le serveur, car, par exemple, le fichier manifeste n’est pas présent, le segment ne peut pas être téléchargé, et ainsi de suite, TVSDK tente d’échouer en essayant les options suivantes :

1. Tentez un basculement vers le même segment, au même débit, dans un fichier de variante.
1. Passez à un autre débit (commutateur ABR) dans le même fichier.
1. Parcourez tous les débits disponibles dans chaque variante disponible.
1. Ignorez le segment et émettez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une notification d’ `CONTENT_ERROR` erreur. Cette notification contient une notification interne avec le `DOWNLOAD_ERROR` code de code. Si le flux avec le problème est une autre piste audio, TVSDK génère la notification `AUDIO_TRACK_ERROR` d’erreur.

Si le moteur vidéo ne parvient pas à obtenir en continu les segments, il limite les sauts de segments continus à 5, après quoi la lecture est arrêtée et TVSDK émet une erreur `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Les paramètres de contrôle de débit binaire adaptatif (ABR) ne sont pas pris en compte lorsqu’un basculement survient. En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit leur  de débit binaire, comme flux de sauvegarde.
>
>Lors d’une opération de basculement, il peut y avoir un commutateur . Si une erreur se produit lors du téléchargement d’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit minimal/maximal autorisé sont ignorés.

