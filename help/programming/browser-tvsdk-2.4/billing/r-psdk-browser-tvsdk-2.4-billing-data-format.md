---
description: Le navigateur TVSDK envoie les mesures de facturation à Adobe dans un format XML.
seo-description: Le navigateur TVSDK envoie les mesures de facturation à Adobe dans un format XML.
seo-title: Transmettre les mesures de facturation
title: Transmettre les mesures de facturation
uuid: ed2638d2-7894-4840-b31a-51e48e0a3f49
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Transmettre les mesures de facturation{#transmit-billing-metrics}

Le navigateur TVSDK envoie les mesures de facturation à Adobe dans un format XML.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Si vous utilisez un outil de capture réseau pour surveiller les statistiques que le navigateur TVSDK transmet à Adobe, vous devriez voir des unités comme celles-ci :

```
<?xml version="1.0" encoding="UTF-8"?>
<request>
    <sc_xml_ver>1.0</sc_xml_ver>
    <reportSuiteID>primesample2</reportSuiteID>
    <visitorID>947310128cb56f41</visitorID>
    <pageURL>https://. . ..m3u8</pageURL>
    <timestamp>2016-4-7T10:1:4</timestamp>
    <contextData>
        <billingMetrics>
            <publisherID>com.adobe.primetime.reference.PrimetimeReference</publisherID>
            <contentType>vod</contentType>
            <adsEnabled>true</adsEnabled>
            <midrollEnabled>true</midrollEnabled>
            <platform>Mac OSX 10.11.5</platform>
            <tvsdkVersion>2,4,0,1559</tvsdkVersion>
            <contentURL>https://. . ..m3u8</contentURL>
        </billingMetrics>
    </contextData>
</request>
```

Les propriétés booléennes `drmProtected`, `adsEnabled`et `midrollEnabled` apparaissent uniquement si elles sont vraies.