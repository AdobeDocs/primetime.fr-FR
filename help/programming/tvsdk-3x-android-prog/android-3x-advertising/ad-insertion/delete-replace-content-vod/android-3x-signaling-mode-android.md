---
description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
uuid: 49abab49-4e52-477d-b7ed-688ee63e7473
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.

>[!TIP]
>
>En cas de conflit entre les plages de temps et les modes de signalisation publicitaire, TVSDK donne la priorité aux plages de temps.

Le tableau suivant fournit des détails sur le mode de signalisation et les comportements de combinaison de métadonnées :

**Carte du serveur**

| **Métadonnées de la publicité** | **Résolveurs créés** | **`PlacementInformations`créé&#x200B;** | **Comportement résultant** |
|--- |--- |--- |--- |
|  | Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Plages supprimées, Publicités insérées |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Publicités insérées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées |
| Marquer | Publicité personnalisée | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | Publicité personnalisée, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |

**Repères de manifeste**

| Métadonnées de la publicité | Résolveurs créés | `PlacementInformations` créé | Comportement résultant |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Publicités insérées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Plages supprimées, publicités insérées |
| Mark, Auditude | Mark, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Marquer | Publicité personnalisée | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées |

**Période personnalisée**

| Métadonnées de la publicité | Résolveurs créés | `PlacementInformations` créé | Comportement résultant |
|--- |--- |--- |--- |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées, aucune publicité insérée |
| Auditude | Auditude | Aucun | Aucune publicité insérée |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées par des publicités |
| Marquer | Publicité personnalisée | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | Publicité personnalisée, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées, aucune publicité insérée |

**Non défini (par défaut)**

| Métadonnées de la publicité | Résolveurs créés | `PlacementInformations` créé | Comportement résultant |
|--- |--- |--- |--- |
| Supprimer | Supprimer | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Plages supprimées |
| Supprimer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Plages supprimées, publicités insérées |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Publicités insérées |
| Remplacer, Auditude | Supprimer, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Plages remplacées par des publicités |
| Marquer | Publicité personnalisée | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |
| Mark, Auditude | Publicité personnalisée, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Plages marquées |