---
description: TVSDK prend des informations de FreeWheel et d’autres serveurs qui fournissent des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise les impressions publicitaires avec une précision qui montre mieux que les créatifs capturent ou négligent les intérêts d’un public.
title: Mesures publicitaires à partir de Moat
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Mesures publicitaires à partir de Moat{#ad-measurements-from-moat}

TVSDK prend des informations de FreeWheel et d’autres serveurs qui fournissent des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise les impressions publicitaires avec une précision qui montre mieux que les créatifs capturent ou négligent les intérêts d’un public.

Moat est un service permettant de mesurer et d’afficher les publicités à plusieurs fins, des navigateurs aux applications. Moat génère des données d’analyse marketing en temps réel sur plusieurs plateformes.

Le code XML de réponse VAST possède une propriété et un élément que votre code peut lire, la propriété d’ID de publicité la plus éloignée et l’élément d’extension le plus éloigné. Dans les deux cas, votre code peut utiliser TVSDK pour enregistrer les informations d’ID de publicité et d’extension et organiser les informations dans une arborescence. Avec cette organisation, votre code peut récupérer les données de n’importe quel niveau et les transmettre à l’endroit où il doit se rendre. La valeur de la propriété d’identifiant de publicité la plus éloignée permet au code de coordonner les informations de la campagne associée.

Par exemple, FreeWheel peut renvoyer des données dans un élément Extensions . Vous trouverez ci-dessous un exemple d’élément .

```xml
<Extensions> 
   <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
     <MeasurementInfo renditionID="6398737" type="MediaFile"> 
      <MoatID> 
       <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
       <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID> 
        <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
        <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions>
```

La roue libre peut également définir la propriété id dans l’élément Ad, comme illustré dans l’exemple ci-dessous.

```
<Ad id="118566" sequence="1">
```

Reportez-vous à la documentation de l’API pour la classe . `PTNetworkAdInfo` in `PTAdAsset`.
