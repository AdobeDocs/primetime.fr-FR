---
description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause et l’inclusion de publicités.
seo-description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause et l’inclusion de publicités.
seo-title: Comportement de lecture par défaut et personnalisé avec les publicités
title: Comportement de lecture par défaut et personnalisé avec les publicités
uuid: cc996e5c-bee2-451b-96cb-088df1694188
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# Comportement de lecture par défaut et personnalisé avec les publicités {#default-and-customized-playback-behavior-with-ads}

Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause et l’inclusion de publicités.

Pour remplacer le comportement par défaut, utilisez `PTAdPolicySelector`.

>[!IMPORTANT]
>
>Pour la VOD et la diffusion en continu directe/linéaire, les ajustements de chronologie ne peuvent pas être modifiés. Cela signifie qu’une publicité ne peut pas être supprimée de la chronologie après sa lecture. Si l’utilisateur effectue une recherche en retour, la même publicité est de nouveau lue, même si la stratégie normale aurait été de la supprimer.

>[!IMPORTANT]
>
>TVSDK ne permet pas de désactiver la recherche pendant les publicités. Adobe vous recommande de configurer votre application pour désactiver la recherche pendant les publicités.

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
   <td colname="col1"> Pendant la lecture normale, une coupure publicitaire est rencontrée. </td> 
   <td colname="col2"></td> 
   <td colname="col3">Spécifiez une autre stratégie pour la coupure publicitaire en utilisant <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche sur les coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Lit la dernière coupure publicitaire non visionnée qui a été ignorée et reprend la lecture à la position de recherche souhaitée lorsque la coupure est terminée. </td> 
   <td colname="col3">Sélectionnez le saut de saut à lire en utilisant <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche en amont sur les coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Ignore la position de recherche souhaitée sans lire les coupures publicitaires. </td> 
   <td colname="col3">Sélectionnez le saut de saut à lire en utilisant <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité au cours de laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique où la recherche s'est terminée en utilisant <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche en amont dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité au cours de laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique dans laquelle la recherche s'est terminée en utilisant <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur les coupures publicitaires surveillées dans le contenu principal. </td> 
   <td colname="col2"> Si la dernière coupure publicitaire ignorée a déjà été visionnée, passe à la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Sélectionnez les pauses sautées à lire à l’aide de <span class="codeph"> selectAdBreaksToPlay</span> et déterminez celles qui ont déjà été visionnées à l’aide de <span class="codeph"> PTAdBreak.isWatched</span>. <p> <p>Important :  Par défaut, TVSDK marque une coupure publicitaire comme visionnée immédiatement après avoir saisi la première publicité de la coupure publicitaire. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur un ou plusieurs coupures publicitaires et passe à une coupure publicitaire surveillée. </td> 
   <td colname="col2"> Ignore la coupure publicitaire et recherche la position immédiatement après la coupure publicitaire. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire (avec l'état de contrôle défini sur true) et pour la publicité spécifique où la recherche s'est terminée à l'aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant sur les publicités insérées à l’aide de marqueurs publicitaires personnalisés. </td> 
   <td colname="col2"> Ignore la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>

