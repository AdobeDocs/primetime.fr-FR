---
description: TVSDK récupère les informations de FreeWheel et d’autres serveurs d’annonces fournissant des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui indique mieux si les créatifs capturent ou négligent les intérêts d’une audience.
title: Mesures publicitaires de Moat
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Mesures publicitaires de Moat{#ad-measurements-from-moat}

TVSDK récupère les informations de FreeWheel et d’autres serveurs d’annonces fournissant des réponses VAST. FreeWheel fournit, dans les réponses VAST, des informations du service Moat. Le service Moat comptabilise et imprime avec une précision qui indique mieux si les créatifs capturent ou négligent les intérêts d’une audience.

Moat est un service permettant de mesurer et d’afficher les données à plusieurs fins, des navigateurs aux applications. Moat génère des données d’analyse marketing en temps réel sur plusieurs plates-formes.

La réponse VAST XML comporte une propriété et un élément que votre code peut lire, la propriété la plus éloignée `Ad id` et l&#39;élément le plus éloigné `Extension`. Dans les deux cas, votre code peut utiliser TVSDK pour enregistrer les informations `Ad id` et `Extension`, puis organiser les informations dans une arborescence. Avec cette organisation, votre code peut récupérer les données de n’importe quel niveau et les transmettre à n’importe quel emplacement. La valeur de la propriété la plus à l&#39;extérieur `Ad id` permet au code de coordonner les informations de la campagne associée.

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

La roue libre peut également définir la propriété `id` dans l&#39;élément `Ad`, comme indiqué dans l&#39;exemple ci-dessous.

```xml
<Ad id="118566" sequence="1">
```

Pour plus d’informations sur l’API, voir la documentation de l’API pour la classe [NetworkAdInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/).
