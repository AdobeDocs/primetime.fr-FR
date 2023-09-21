---
description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalement des publicités et combinaisons de métadonnées de publicité. Différentes combinaisons de mode de signalement et de métadonnées génèrent des comportements différents.
title: Effet sur l’insertion et la suppression de publicités à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Effet sur l’insertion et la suppression de publicités à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalement des publicités et combinaisons de métadonnées de publicité. Différentes combinaisons de mode de signalement et de métadonnées génèrent des comportements différents.

>[!TIP]
>
>En cas de conflit entre les périodes et les modes de signalisation publicitaire, TVSDK donne la priorité aux périodes.

Le tableau suivant fournit des détails sur le mode de signalisation et les comportements de combinaison de métadonnées :

**Carte du serveur**

| **Métadonnées de publicité** | **Résolveurs créés** | **`PlacementInformations`created** | **Comportement résultant** |
|--- |--- |--- |--- |
|  | Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Plages supprimées, Publicités insérées |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Publicités insérées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées |
| Marquer | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |

**Cotes du manifeste**

| Métadonnées de publicité | Résolveurs créés | `PlacementInformations` created | Comportement résultant |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Publicités insérées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Plages supprimées, publicités insérées |
| Mark, Auditude | Mark, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Marquer | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées |

**Période personnalisée**

| Métadonnées de publicité | Résolveurs créés | `PlacementInformations` created | Comportement résultant |
|--- |--- |--- |--- |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées, aucune publicité insérée |
| Auditude | Auditude | Aucun | Aucune publicité insérée |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées par des publicités |
| Marquer | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | Publicité personnalisée, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |

**Non défini (par défaut)**

| Métadonnées de publicité | Résolveurs créés | `PlacementInformations` created | Comportement résultant |
|--- |--- |--- |--- |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Plages supprimées, publicités insérées |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Publicités insérées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées par des publicités |
| Marquer | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
