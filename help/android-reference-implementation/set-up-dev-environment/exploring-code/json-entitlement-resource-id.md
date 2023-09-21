---
title: Objet JSON pour l’ID de ressource de droit
description: Le bloc de code suivant fournit un exemple d’objet JSON lorsque l’ID de ressource de droit est une chaîne de texte simple.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Objet JSON pour l’ID de ressource de droit {#json-object-for-entitlement-resource-id}

Le bloc de code suivant fournit un exemple d’objet JSON lorsque l’ID de ressource de droit est une chaîne de texte simple. Dans ce cas, l’ID de ressource est la chaîne &quot;resource&quot;.

```
"metadata" : { 
"entitlement" : { 
"id" : "resource" 
} 
}
```

Le bloc de code suivant fournit un exemple d’objet JSON lorsque l’ID de ressource de droit est une chaîne mRSS codée en HTML.

```
<rss version="2.0" xmlns:media="https://search.yahoo.com/mrss/"> 
<channel> 
<title>REF_ADOBE</title> 
<item> 
<title>Adobe Primetime Reference</title> 
<guid>1234</guid> 
<media:rating scheme="urn:v-chip">TV-PG</media:rating> 
</item> 
</channel> 
</rss>
```

La chaîne mRSS suivante est utilisée comme ID de ressource.

```
"metadata" : { 
    "entitlement" : { 
        "id" : "<rss version=&quot;2.0&quot; 
        xmlns:media=&quot; 
        https://search.yahoo.com/mrss/&quot; 
        ><channel><title>REF_ADOBE</title><item> 
        <title>Adobe Primetime Reference</title><guid> 
        1234</guid><media:rating scheme=&quot;urn:v-chip&quot;> 
        TV-PG</media:rating></item></channel></rss>" 
        } 
} 
```
