---
description: Voici quelques informations et exemples sur la façon dont le SDK du navigateur prend en charge les manifestes originaux mis à jour.
seo-description: Voici quelques informations et exemples sur la façon dont le SDK du navigateur prend en charge les manifestes originaux mis à jour.
seo-title: Architecture de mise à jour de manifeste principal en direct
title: Architecture de mise à jour de manifeste principal en direct
uuid: 6f253502-8dec-4b42-9ee1-99ad9bfd6080
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Architecture de mise à jour de manifeste principal en direct{#live-master-manifest-update-architecture}

Voici quelques informations et exemples sur la façon dont le SDK du navigateur prend en charge les manifestes originaux mis à jour.

Par défaut, cette fonction est désactivée. Si votre application l’active en définissant une fréquence de mise à jour en minutes, les étapes suivantes se produisent après chaque intervalle de mise à jour :

1. Le navigateur TVSDK vérifie l’heure de dernière modification du manifeste principal et l’étiquette pour déterminer si le fichier a été mis à jour.

   Si l’heure et l’étiquette ont changé, le fichier est considéré comme modifié.
1. Le navigateur TVSDK analyse et analyse le nouveau manifeste et prend les mesures appropriées en fonction de la nature de la mise à jour.
1. Si le débit de lecture actuel correspond au débit du manifeste modifié, le navigateur TVSDK bascule sur le nouveau profil.

   Le nouveau profil peut provenir d’un serveur différent ou du même serveur, à la même vitesse de transmission. Dans ce cas, la transition est lisse.
1. Si le débit de lecture actuel n’est plus présent dans le nouveau manifeste, le navigateur TVSDK tente de trouver un débit dans le profil actuel qui existe également dans le nouveau manifeste.

   * Si une correspondance est trouvée, le lecteur passe d’abord au profil de débit correspondant dans le manifeste existant et passe au profil de débit correspondant dans le manifeste mis à jour. Ainsi, la transition est lisse.
   * S’il n’y a pas de débit commun entre le manifeste précédent et le nouveau manifeste, ou si le SDK du navigateur ne peut pas passer au débit correspondant, le SDK du navigateur bascule directement sur le profil de débit le plus faible du nouveau manifeste et utilise ABR pour passer à tout débit autorisé en fonction de la bande passante. Cela peut provoquer un léger problème de lecture mais devrait avoir un impact minimal.

1. Si la mise à jour réussit, le navigateur TVSDK distribue un `MediaPlayerItemEvent.MASTER_UPDATED` événement.
1. Si la mise à jour échoue, la lecture se poursuit avec la configuration antérieure à cette mise à jour.

## Exemple 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

Les débits suivants diffusent en direct :

* 500k
* 900k
* 2100k

Le flux de 2100k présente certains problèmes, il doit donc être redémarré. Le manifeste principal est mis à jour pour ne contenir que 500 k et 900 k. Peu de temps après, les utilisateurs qui regardent ce programme à 2100k vont subir un basculement de débit à 900k. Les utilisateurs qui regardent à 900k continuent à regarder à 900k. Par la suite, le flux de 2 100 000 reprend et est de nouveau ajouté dans le manifeste principal. Un moment plus tard, les utilisateurs qui regardent à 900 k, et qui ont la bande passante, sont passés à 2100 k.

### Exemple 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

Les débits suivants diffusent en direct :

* 500k
* 900k
* 2100k

Tous ces débits doivent être redémarrés. Il y a deux courants temporels pour cela, à 400 k et 1500 k. Les utilisateurs passent à 400 Ko, soit le débit binaire le plus faible de la nouvelle configuration. Certains utilisateurs passent à 1500k lorsque leur bande passante est suffisante. Par la suite, les débits de trois bits sont sauvegardés et le manifeste principal est mis à jour. Les utilisateurs reviennent automatiquement à la surveillance à 500 Ko, ce qui représente la bande passante la plus basse du manifeste révisé (original). Un certain temps plus tard, les utilisateurs passent à la bande passante la plus élevée (900 k ou 1200 k) que leur réseau leur permet.

<!-- 

WRITER: Add relref to api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#MASTER_UPDATED

 -->

