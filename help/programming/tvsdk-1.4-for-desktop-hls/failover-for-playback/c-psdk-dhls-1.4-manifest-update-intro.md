---
description: TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de profils de débit binaire à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires profils non chevauchants entre les mises à jour.
seo-description: TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de profils de débit binaire à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires profils non chevauchants entre les mises à jour.
seo-title: Mise à jour du manifeste principal en direct
title: Mise à jour du manifeste principal en direct
uuid: 44f8adc2-0538-4c5d-8e39-55f661d8540b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise à jour du manifeste principal en direct{#live-master-manifest-update}

TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de profils de débit binaire à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les débits binaires profils non chevauchants entre les mises à jour.

Les fonctionnalités suivantes sont prises en charge :

* Nombre de Profils (augmentation ou diminution)
* Débit du Profil (chevauchement ou non)
* Profils avec des URL sur le même (ou sur des serveurs différents)
* Toute structure de basculement

Toutes les conditions suivantes doivent être remplies :

* Le flux est en direct.
* Le temps et l&#39;étag changent.
* Toutes les informations sur le rendu restent les mêmes (sauf que les URL peuvent varier).
* Les informations d’accès DRM restent les mêmes.
* Les segments sont regroupés autour des mêmes limites PTS et cadres dans une petite plage d’erreurs.

## Architecture de mise à jour de manifeste principal en direct {#section_32254A0F684B4960ACC33BF6B1AEF6F1}

Voici quelques informations et exemples sur la façon dont TVSDK prend en charge les manifestes originaux mis à jour.

Par défaut, cette fonction est désactivée. Si votre application l’active en définissant une fréquence de mise à jour en minutes, les étapes suivantes se produisent après chaque intervalle de mise à jour :

1. TVSDK vérifie l’heure de dernière modification du manifeste principal et l’étiquette pour déterminer si le fichier a été mis à jour.

   Si l’heure et l’étiquette ont changé, le fichier est considéré comme modifié.
1. TVSDK analyse et analyse le nouveau manifeste et prend les mesures appropriées en fonction de la nature de la mise à jour.
1. Si le débit de lecture actuel correspond au débit du manifeste modifié, TVSDK passe au nouveau profil.

   Le nouveau profil peut provenir d’un serveur différent ou du même serveur, à la même vitesse de transmission. Dans ce cas, la transition est lisse.
1. Si le débit de lecture actuel n’est plus présent dans le nouveau manifeste, TVSDK tente de trouver un débit dans le profil actuel qui existe également dans le nouveau manifeste.

   * Si une correspondance est trouvée, le lecteur passe d’abord au profil de débit correspondant dans le manifeste existant et passe au profil de débit correspondant dans le manifeste mis à jour. Ainsi, la transition est lisse.
   * S’il n’y a pas de débit commun entre le manifeste précédent et le nouveau manifeste, ou si TVSDK ne peut pas passer au débit correspondant, TVSDK bascule directement sur le profil de débit le plus faible du nouveau manifeste et utilise ABR pour basculer à tout débit autorisé basé sur la bande passante. Cela peut provoquer un léger problème de lecture mais devrait avoir un impact minimal.

1. Si la mise à jour réussit, TVSDK distribue un `MediaPlayerItemEvent.MASTER_UPDATED` événement.
1. Si la mise à jour échoue, la lecture se poursuit avec la configuration antérieure à cette mise à jour.

### Exemple 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

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

## Utiliser la mise à jour de manifeste principal en direct {#section_34AC4A9751DB4B7C8561302C6A59A1C4}

Vous pouvez activer cette fonction et vérifier si des événements connexes sont associés.

1. Pour activer les mises à jour du manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la `NetworkConfiguration.masterUpdateInterval` propriété.
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant le `MediaPlayerItemEvent.MASTER_UPDATED` événement.

