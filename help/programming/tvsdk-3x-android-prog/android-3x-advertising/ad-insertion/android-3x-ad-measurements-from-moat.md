---
description: TVSDK récupère les informations de FreeWheel et d’autres serveurs d’annonces fournissant des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux si les créatifs capturent ou négligent un   d'intérêt.
seo-description: TVSDK récupère les informations de FreeWheel et d’autres serveurs d’annonces fournissant des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux si les créatifs capturent ou négligent un   d'intérêt.
seo-title: Mesures publicitaires de Moat
title: Mesures publicitaires de Moat
uuid: 4de4ea5e-ef52-4b6b-b215-7601a2dfdb96
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Mesures publicitaires de Moat {#ad-measurements-from-moat}

TVSDK récupère les informations de FreeWheel et d’autres serveurs d’annonces fournissant des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux si les créatifs capturent ou négligent un   d&#39;intérêt.

Moat est un service permettant de mesurer et d’afficher les données à plusieurs fins, des navigateurs aux applications. Moat génère des données d’analyse marketing en temps réel sur plusieurs plateformes.

Le XML de réponse VAST possède une propriété et un élément que votre code peut lire, la `Ad id` propriété la plus à l’extérieur et l’ `Extension` élément le plus à l’extérieur. Dans les deux cas, votre code peut utiliser TVSDK pour enregistrer les `Ad id` informations et les `Extension` informations, puis organiser les informations dans une arborescence. Avec cette organisation, votre code peut récupérer les données de n’importe quel niveau et les transmettre à n’importe quel endroit. La valeur de la `Ad id` propriété ultrapériphérique permet au code de coordonner les informations de la campagne associée.

Par exemple, FreeWheel peut renvoyer des données dans un élément Extensions. Vous trouverez ci-dessous un exemple d’élément.

```xml
<?xml version="1.0"?> 
<Extensions> 
  <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
      <MeasurementInfo renditionID="6398737" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions> 
```

La roue libre peut également définir la `id` propriété dans l’ `Ad` élément, comme illustré dans l’exemple ci-dessous.

```xml
<Ad id="118566" sequence="1">
```

Pour plus d’informations sur l’API, voir la documentation de l’API pour la classe `NetworkAdInfo`.