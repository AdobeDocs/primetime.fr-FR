---
description: TVSDK envoie les mesures de facturation à Adobe dans un format XML.
seo-description: TVSDK envoie les mesures de facturation à Adobe dans un format XML.
seo-title: Transmettre les mesures de facturation
title: Transmettre les mesures de facturation
uuid: f4a7f50e-f457-434e-bf26-1e06cb15a038
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Transmettre les mesures de facturation {#transmit-billing-metrics}

TVSDK envoie les mesures de facturation à Adobe dans un format XML.

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

Si vous utilisez un outil de capture réseau pour surveiller les statistiques que TVSDK transmet à Adobe, vous devriez voir des unités comme celles-ci :

```xml
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