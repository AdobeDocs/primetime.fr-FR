---
description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause et l’inclusion de publicité.
title: Comportement de lecture par défaut et personnalisé avec les publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Comportement de lecture par défaut et personnalisé avec les publicités{#default-and-customized-playback-behavior-with-ads}

Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause et l’inclusion de publicité.

Pour remplacer le comportement par défaut, utilisez `PTAdPolicySelector`.

>[!IMPORTANT]
>
>Pour la diffusion VOD et la diffusion en continu directe/linéaire, les ajustements de chronologie ne peuvent pas être modifiés. Cela signifie qu’une publicité ne peut pas être supprimée de la chronologie après sa lecture. Si l’utilisateur effectue une recherche en amont, la même publicité est relue même si la stratégie normale aurait été de la supprimer.

>[!IMPORTANT]
>
>TVSDK ne permet pas de désactiver la recherche pendant les publicités. Adobe recommande de configurer votre application pour désactiver la recherche pendant les publicités.

Le tableau suivant décrit comment TVSDK gère les publicités et les coupures publicitaires pendant la lecture :

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Activité vidéo </th> 
   <th colname="col2" class="entry"> Stratégie de comportement TVSDK par défaut </th> 
   <th colname="col3" class="entry">Personnalisation disponible via <span class="codeph"> PTAdPolicySelector</span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Lors de la lecture normale, une coupure publicitaire se produit. </td> 
   <td colname="col2"></td> 
   <td colname="col3">Spécifiez une autre stratégie pour la coupure publicitaire à l’aide de <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche au-dessus de la ou des coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Lit la dernière coupure publicitaire non visionnée qui a été sautée et reprend la lecture à la position de recherche souhaitée lorsque la coupure est terminée. </td> 
   <td colname="col3">Sélectionnez la coupure ignorée à lire à l’aide de <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’arrière par rapport aux coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Ignore la position de recherche souhaitée sans lire les coupures publicitaires. </td> 
   <td colname="col3">Sélectionnez la coupure ignorée à lire à l’aide de <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité dans laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique où la recherche s’est terminée à l’aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’arrière dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité dans laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique dans laquelle la recherche s’est terminée en utilisant <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur les coupures publicitaires visionnées dans le contenu principal. </td> 
   <td colname="col2"> Si la dernière coupure publicitaire ignorée a déjà été visionnée, passe à la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Sélectionnez les pauses ignorées à l’aide de <span class="codeph"> selectAdBreaksToPlay</span> et déterminer les coupures qui ont déjà été visionnées à l’aide de <span class="codeph"> PTAdBreak.isWatched</span>. <p> <p>Important : Par défaut, TVSDK marque une coupure publicitaire comme vue immédiatement après la première publicité dans la coupure publicitaire. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur une ou plusieurs coupures publicitaires et passe à une coupure publicitaire surveillée. </td> 
   <td colname="col2"> Ignore la coupure publicitaire et recherche la position immédiatement après la coupure publicitaire. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire (avec l’état de contrôle défini sur true) et pour la publicité spécifique où la recherche s’est terminée à l’aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant par rapport aux publicités qui ont été insérées à l’aide de marqueurs publicitaires personnalisés. </td> 
   <td colname="col2"> Ignore la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>
