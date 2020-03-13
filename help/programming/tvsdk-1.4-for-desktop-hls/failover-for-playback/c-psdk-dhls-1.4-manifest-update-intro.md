---
description: TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de de débit binaire lorsque le apparaît ou disparaît du manifeste principal, y compris les débits binaires non superposés entre les mises à jour.
seo-description: TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de de débit binaire lorsque le apparaît ou disparaît du manifeste principal, y compris les débits binaires non superposés entre les mises à jour.
seo-title: Mise à jour du manifeste original en direct
title: Mise à jour du manifeste original en direct
uuid: 44f8adc2-0538-4c5d-8e39-55f661d8540b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise à jour du manifeste original en direct{#live-master-manifest-update}

TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 originaux pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de de débit binaire lorsque le apparaît ou disparaît du manifeste principal, y compris les débits binaires non superposés entre les mises à jour.

Les fonctionnalités suivantes sont prises en charge :

* Nombre de  (augmentation ou diminution)
* Débit  (chevauchement ou non)
*  avec des URL sur le même (ou sur des serveurs différents)
* Toute structure de basculement

Toutes les conditions suivantes doivent être remplies :

* Le flux est en direct.
* Le temps et l&#39;étag changent.
* Toutes les informations sur le rendu restent les mêmes (sauf que les URL peuvent varier).
* Les informations d’accès DRM restent les mêmes.
* Les segments sont regroupés autour des mêmes limites PTS et cadres dans une petite plage d’erreurs.

## Architecture de mise à jour du manifeste principal en direct {#section_32254A0F684B4960ACC33BF6B1AEF6F1}

Voici quelques informations et exemples sur la manière dont le SDK TVSDK prend en charge les manifestes originaux mis à jour.

Par défaut, cette fonction est désactivée. Si votre application l’active en définissant une fréquence de mise à jour en minutes, les étapes suivantes se produisent après chaque intervalle de mise à jour :

1. Le kit TVSDK vérifie l’heure de dernière modification du manifeste principal et l’étiquette afin de déterminer si le fichier a été mis à jour.

   Si l’heure et l’étiquette ont changé, le fichier est considéré comme modifié.
1. Le TVSDK analyse et analyse le nouveau manifeste et prend les mesures appropriées en fonction de la nature de la mise à jour.
1. Si le débit binaire en cours de lecture correspond au débit binaire du manifeste modifié, le kit TVSDK bascule vers le nouvel .

   Le nouveau peut provenir d’un serveur différent ou du même serveur, au même débit. Dans ce cas, le  est lisse.
1. Si le débit binaire en cours de lecture n’est plus présent dans le nouveau manifeste, le kit TVSDK tente de trouver un débit binaire dans le  actuel qui existe également dans le nouveau manifeste.

   * Si une correspondance est trouvée, le lecteur bascule d’abord vers le de débit correspondant dans le manifeste existant et bascule vers le de débit correspondant  dans le manifeste mis à jour. Cela permet de s’assurer que le  est lisse.
   * S’il n’existe aucun débit commun entre le manifeste précédent et le nouveau manifeste, ou si le TVSDK ne peut pas passer au débit qui correspond, le TVSDK bascule directement sur le de débit le plus faible du nouveau manifeste et utilise ABR pour passer à un débit autorisé basé sur la bande passante. Cela peut entraîner un léger problème au niveau de la lecture, mais devrait avoir un impact minimal.

1. Si la mise à jour réussit, le kit TVSDK distribue un `MediaPlayerItemEvent.MASTER_UPDATED` .
1. Si la mise à jour échoue, la lecture se poursuit avec la configuration d’avant cette mise à jour.

### Exemple 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

Les débits suivants diffusent en direct :

* 500k
* 900k
* 2100k

Le flux 2100 000 contient des problèmes, il doit donc être redémarré. Le manifeste principal est mis à jour pour ne contenir que 500 Ko et 900 Ko. Peu de temps après, les utilisateurs qui regardent ce à 2100k verront un changement de débit de 900k. Les utilisateurs qui regardent à 900k continuent à regarder à 900k. Par la suite, le flux de 2 100 000 reprend et est ajouté à nouveau dans le manifeste principal. Un moment plus tard, les utilisateurs qui regardent à 900k, et qui ont la bande passante, passent à 2100k.

### Exemple 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

Les débits suivants diffusent en direct :

* 500k
* 900k
* 2100k

Tous ces débits doivent être redémarrés. Il y a deux flux temporels configurés pour cela, à 400k et 1500k. Les utilisateurs passent à 400 Ko, soit le débit binaire le plus faible de la nouvelle configuration. Certains utilisateurs passent à 1500k lorsque leur bande passante est suffisante. Par la suite, les débits des trois bits sont rétablis et le manifeste principal est mis à jour. Les utilisateurs reviennent automatiquement à la surveillance à 500 Ko, soit la bande passante la plus basse du manifeste révisé (original). Un moment plus tard, les utilisateurs passent à la bande passante la plus élevée (900 k ou 1 200 k) que leur réseau leur permet.

## Utilisation de la mise à jour de manifeste maître en direct {#section_34AC4A9751DB4B7C8561302C6A59A1C4}

Vous pouvez activer cette fonctionnalité et rechercher les  de connexes.

1. Pour activer les mises à jour de manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la `NetworkConfiguration.masterUpdateInterval` propriété.
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant le  du `MediaPlayerItemEvent.MASTER_UPDATED` .

