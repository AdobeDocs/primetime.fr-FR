---
description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-description: Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.
seo-title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
title: Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires
uuid: 7b2a5588-110d-4ce5-aa9c-706d357f211d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Effet sur l’insertion et la suppression d’une publicité à partir du mode de signalisation publicitaire et des combinaisons de métadonnées publicitaires {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

Vous pouvez marquer, supprimer et remplacer des plages de temps dans les flux VOD en utilisant différents modes de signalisation publicitaire et combinaisons de métadonnées publicitaires. Différentes combinaisons de mode de signalisation et de métadonnées entraînent des comportements différents.

>[!TIP]
>
>En cas de conflit entre les plages de temps et les modes de signalisation publicitaire, TVSDK donne la priorité aux plages de temps.

Le tableau suivant fournit des détails sur le mode de signalisation et les comportements de combinaison de métadonnées :

<table id="table_6044AA1ACFA244FA814EA2D0766C6D12"> 
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
   <td colname="1"> <p><b>Carte du serveur</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
    <ul id="ul_E0A2F885E93B4D23A486C37B305E17D8"> 
     <li id="li_D977B398D3904A44AFEC4B05AB0E3340"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li id="li_439886CB38AA46239C2E40352443888A"><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
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
   <td colname="1"> <p><b>Repères de manifeste</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
    <ul id="ul_2DD298538E9344B9BAB882485BB57747"> 
     <li id="li_F39A69EFA7ED45C18978A2C462AF7641"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li id="li_8CCDA3B1C63F4BC396F28F443D8C42F8"><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
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
   <td colname="1"> <p><b>Période personnalisée</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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
   <td colname="1"> <p><b>Non défini (par défaut)</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
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

