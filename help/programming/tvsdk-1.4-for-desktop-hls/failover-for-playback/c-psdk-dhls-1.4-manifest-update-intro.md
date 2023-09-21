---
description: TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 maîtres pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de profils de débit au fur et à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les taux de bit de profil non chevauchants entre les mises à jour.
title: Mise à jour du manifeste principal en direct
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Mise à jour du manifeste principal en direct{#live-master-manifest-update}

TVSDK peut détecter les informations de lecture modifiées dans les manifestes m3u8 maîtres pour la diffusion en direct et mettre à jour les informations de lecture pendant la lecture du flux. TVSDK prend en charge un ensemble dynamique de profils de débit au fur et à mesure que les profils apparaissent ou disparaissent du manifeste principal, y compris les taux de bit de profil non chevauchants entre les mises à jour.

Les fonctionnalités suivantes sont prises en charge :

* Nombre de profils (augmentation ou diminution)
* Débit binaire du profil (chevauchement ou non)
* Profils avec des URL sur le même (ou sur des serveurs différents)
* Toute structure de basculement

Toutes les conditions suivantes doivent être remplies :

* Le flux est en direct.
* L&#39;heure et l&#39;etag ont changé.
* Toutes les informations de rendu restent identiques (sauf que les URL peuvent varier).
* Les informations d’accès DRM restent identiques.
* Les segments sont conditionnés autour des mêmes limites de texte et de cadre dans une petite plage d’erreurs.

## Architecture de mise à jour du manifeste principal en direct {#section_32254A0F684B4960ACC33BF6B1AEF6F1}

Voici quelques informations et exemples sur la manière dont TVSDK prend en charge les manifestes maîtres mis à jour.

Cette fonctionnalité est désactivée par défaut. Si votre application l’active en définissant une fréquence de mise à jour en minutes, les étapes suivantes se produisent après chaque intervalle de mise à jour :

1. TVSDK vérifie l’heure de dernière modification du manifeste principal et l’etag pour déterminer si le fichier a été mis à jour.

   Si l’heure et l’etag ont changé, le fichier est considéré comme modifié.
1. TVSDK analyse et analyse le nouveau manifeste et prend les mesures appropriées en fonction de la nature de la mise à jour.
1. Si le débit de lecture actuel correspond au débit du manifeste modifié, TVSDK passe au nouveau profil.

   Le nouveau profil peut provenir d’un serveur différent ou du même serveur, au même débit. Dans ce cas, la transition est fluide.
1. Si le débit de lecture actuel n’est plus présent dans le nouveau manifeste, TVSDK tente de trouver un débit dans le profil actuel qui existe également dans le nouveau manifeste.

   * Si une correspondance est trouvée, le lecteur bascule d’abord vers le profil de débit correspondant dans le manifeste existant et passe au profil de débit correspondant dans le manifeste mis à jour. Cela garantit que la transition est fluide.
   * S’il n’existe aucun débit commun entre le manifeste précédent et le nouveau manifeste, ou si le TVSDK ne peut pas passer au débit correspondant, le TVSDK passe directement au profil de débit le plus faible du nouveau manifeste et utilise ABR pour passer à un débit autorisé en fonction de la bande passante. Cela peut entraîner un léger problème lors de la lecture, mais devrait avoir un impact minimal.

1. Si la mise à jour est réussie, le TVSDK envoie une `MediaPlayerItemEvent.MASTER_UPDATED` .
1. Si la mise à jour échoue, la lecture se poursuit avec la configuration d’avant cette mise à jour.

### Exemple 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

Les débit binaires suivants diffusent en direct :

* 500k
* 900k
* 2100k

Le flux de 2100k a quelques problèmes, il doit donc être redémarré. Le manifeste principal est mis à jour pour ne contenir que 500 et 900 Ko. Peu de temps après, les utilisateurs qui regardent ce programme à 2100 000 vont subir un basculement de débit à 900 000. Les utilisateurs qui regardent à 900k continuent à regarder à 900k. Par la suite, le flux de 2 100 000 reprend et il est de nouveau ajouté au manifeste principal. Un moment plus tard, les utilisateurs qui regardent à 900 000, et qui ont la bande passante, passent à 2 100 000.

### Exemple 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

Les débit binaires suivants diffusent en direct :

* 500k
* 900k
* 2100k

Tous ces débits doivent être redémarrés. Il y a deux flux temporels configurés pour cela, à 400 000 et 1 500 000. Les utilisateurs passent à 400k, qui est le débit le plus faible de la nouvelle configuration. Certains utilisateurs passent à 1500k lorsque leur bande passante est suffisante. Par la suite, les taux de trois bits sont à nouveau augmentés et le manifeste principal est mis à jour. Les utilisateurs rebasent automatiquement pour regarder à 500 000, soit la bande passante la plus faible du manifeste révisé (d’origine). Un certain temps plus tard, les utilisateurs passent à la bande passante la plus élevée (900 ou 1 200 Ko) que leur réseau leur permet.

## Utilisation de la mise à jour du manifeste principal actif {#section_34AC4A9751DB4B7C8561302C6A59A1C4}

Vous pouvez activer cette fonction et rechercher les événements associés.

1. Pour activer les mises à jour de manifeste principal en direct, définissez la fréquence de mise à jour (en minutes) en définissant la variable `NetworkConfiguration.masterUpdateInterval` .
1. Si vous le souhaitez, effectuez le suivi des mises à jour de manifeste réussies en écoutant les `MediaPlayerItemEvent.MASTER_UPDATED` .
