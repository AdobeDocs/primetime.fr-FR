---
title: Règles de réécriture et de récupération des publicités du manifeste
description: Règles de réécriture et de récupération des publicités du manifeste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Règles de réécriture et de récupération des publicités du manifeste {#manifest-rewriting}

L’Ad Insertion Primetime peut réécrire des fragments et récupérer des ressources à l’aide de règles de recherche/remplacement simples.  Vous pouvez l’utiliser pour effectuer une conversion descendante de https en requêtes http, ce qui augmenterait les performances en supprimant les poignées de main TLS.  Vous pouvez également l’utiliser pour diffuser des ressources publicitaires et cdn à partir du même réseau de diffusion de contenu.

Les règles sont définies comme recherche/remplacement d’expression régulière et peuvent être utilisées pour transformer des URL avant leur envoi, ainsi qu’après leur insertion dans un manifeste.

Cet exemple de règle convertit toutes les requêtes de publicité en domain.com de https vers http.

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

La règle suivante utilise le réseau de diffusion de contenu pour diffuser des publicités qui se trouvent sur le réseau de diffusion de contenu de stockage d’annonces d’Adobe.

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

Les règles peuvent être nommées et activées/désactivées en modifiant la variable `ptprotoswitch` dans l’API du Bootstrap, qui est une liste de règles à exécuter séparées par des virgules.  Par exemple, ces deux règles peuvent être exécutées en définissant `ptprotoswitch=adfetch_rule1,adfetch_rule2`:

```
<ruleSet>
    <rule name="rule1">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
    <rule name="rule2">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
</ruleSet>
```

Contactez votre support technique pour créer/activer ces règles pour votre compte.
