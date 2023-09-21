---
description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalement des publicités et combinaisons de métadonnées de publicité. Différentes combinaisons de mode de signalement et de métadonnées génèrent des comportements différents.
title: Effet sur l’insertion et la suppression de publicités à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Effet sur l’insertion et la suppression de publicités à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalement des publicités et combinaisons de métadonnées de publicité. Différentes combinaisons de mode de signalement et de métadonnées génèrent des comportements différents.

>[!NOTE]
>
>En cas de conflit entre les périodes et les modes de signalisation publicitaire, TVSDK donne la priorité aux périodes.

**Tableau 3 : Mode de signature/Comportements de combinaison de métadonnées**

<table>  
 <thead> 
  <tr> 
   <th class="entry"> Mode de signature des publicités </th> 
   <th class="entry"> Métadonnées de publicité </th> 
   <th class="entry"> Résolveurs créés </th> 
   <th class="entry"><span class="codeph"> PlacementInformations</span> created </th> 
   <th class="entry"> Comportement résultant </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <b>Carte du serveur</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> Supprimer </td> 
   <td> Supprimer </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Plages supprimées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Plages supprimées, Publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Remplacer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Plages remplacées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Marquer </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées, aucune publicité insérée </td> 
  </tr> 
  <tr> 
   <td> <b>Cotes du manifeste</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </td> 
   <td> Publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> Plages supprimées, publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Mark, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées, aucune publicité insérée </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer </td> 
   <td> Supprimer </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Plages supprimées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Marquer </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Remplacer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Plages remplacées </td> 
  </tr> 
  <tr> 
   <td> <b>Période personnalisée</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer </td> 
   <td> Supprimer </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Plages supprimées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Plages supprimées, aucune publicité insérée </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td> Aucun </td> 
   <td> Aucune publicité insérée </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Remplacer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Plages remplacées par des publicités </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Marquer </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Publicité personnalisée, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées, aucune publicité insérée </td> 
  </tr> 
  <tr> 
   <td> <b>Non défini (par défaut)</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer </td> 
   <td> Supprimer </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> Plages supprimées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Supprimer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Plages supprimées, publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> Publicités insérées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Remplacer, Auditude </td> 
   <td> Supprimer, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> Plages remplacées par des publicités </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Marquer </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> CustomAd, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
 </tbody> 
</table>
