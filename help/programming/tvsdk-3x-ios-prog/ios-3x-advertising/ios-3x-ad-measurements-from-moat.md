---
description: TVSDK récupère les informations de FreeWheel et d'autres serveurs qui fournissent des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux que les créatifs capturent ou négligent les intérêts d’une audience.
seo-description: TVSDK récupère les informations de FreeWheel et d'autres serveurs qui fournissent des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux que les créatifs capturent ou négligent les intérêts d’une audience.
seo-title: Mesures publicitaires de Moat
title: Mesures publicitaires de Moat
uuid: 520d33b0-2218-4f74-9689-b9dc520f29cc
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Mesures publicitaires de Moat {#ad-measurements-from-moat}

TVSDK récupère les informations de FreeWheel et d&#39;autres serveurs qui fournissent des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui montre mieux que les créatifs capturent ou négligent les intérêts d’une audience.

Moat est un service permettant de mesurer et d’afficher les données à plusieurs fins, des navigateurs aux applications. Moat génère des données d’analyse marketing en temps réel sur plusieurs plates-formes.

La réponse VAST XML comporte une propriété et un élément que votre code peut lire, la propriété ad id la plus à l’extérieur et l’élément d’extension la plus à l’extérieur. Dans les deux cas, votre code peut utiliser TVSDK pour enregistrer à la fois les informations d’identification de la publicité et les informations d’extension et organiser les informations dans une arborescence. Avec cette organisation, votre code peut récupérer les données de n’importe quel niveau et les transmettre à n’importe quel emplacement. La valeur de la propriété d’ID d’annonce la plus à l’extérieur permet au code de coordonner les informations de la campagne associée.

Par exemple, FreeWheel peut renvoyer des données dans un élément Extensions. Vous trouverez ci-dessous un exemple d’élément.

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

La roue libre peut également définir la propriété id dans l’élément Publicité, comme illustré dans l’exemple ci-dessous.

```
<Ad id="118566" sequence="1">
```

Reportez-vous à la documentation de l&#39;API pour la classe `PTNetworkAdInfo` dans `PTAdAsset`.