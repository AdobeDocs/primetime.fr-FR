---
description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
uuid: c2ae8148-889d-46ae-848a-5f45d993a0e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.

>[!NOTE]
>
>En cas de conflit entre les plages de temps et les modes de signalisation publicitaire, TVSDK donne la priorité aux plages de temps.

**Tableau 3 : Comportements de combinaison Mode de signature/Métadonnées**

<table>  
 <thead> 
  <tr> 
   <th class="entry"> Mode de signature de publicité </th> 
   <th class="entry"> Métadonnées de la publicité </th> 
   <th class="entry"> Résolveurs créés </th> 
   <th class="entry"><span class="codeph"> PlacementInformations</span> créées </th> 
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
   <td> Publicité personnalisée </td> 
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
   <td> <b>Repères de manifeste</b> </td> 
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
   <td> Publicité personnalisée </td> 
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
   <td> Publicité personnalisée </td> 
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
   <td> Publicité personnalisée </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark, Auditude </td> 
   <td> Publicité personnalisée, Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> Plages marquées </td> 
  </tr> 
 </tbody> 
</table>

