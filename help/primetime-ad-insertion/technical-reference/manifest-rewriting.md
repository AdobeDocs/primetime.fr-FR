---
title: Règles de réécriture et de récupération de publicités dans le manifeste
description: 'Règles de réécriture et de récupération de publicités dans le manifeste '
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Règles de réécriture et de récupération des publicités {#manifest-rewriting}

L’Ad Insertion Primetime peut réécrire des fragments et récupérer des ressources à l’aide de règles de recherche/remplacement simples.  Vous pouvez l’utiliser pour effectuer une conversion descendante de https en requêtes http, ce qui augmenterait les performances en supprimant les poignées de main TLS.  Vous pouvez également l’utiliser pour diffuser des ressources publicitaires et des ressources cdn à partir du même réseau de diffusion de contenu.

Les règles sont définies comme des recherches/remplacements d&#39;expression réguliers et peuvent être utilisées pour transformer les URL avant leur envoi, ainsi qu&#39;après leur insertion dans un manifeste.

Cet exemple de règle convertit toutes les requêtes d&#39;annonce en domaine.com de https en http.

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

La règle suivante utilise le CDN de contenu pour diffuser les publicités qui se trouvent sur le CDN de l&#39;Adobe et de l&#39;enregistrement.

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

Les règles peuvent être nommées et activées/désactivées en modifiant le paramètre `ptprotoswitch` dans l&#39;API du Bootstrap, qui est une liste de règles à exécuter séparée par des virgules.  Par exemple, ces deux règles peuvent toutes deux être exécutées en définissant `ptprotoswitch=adfetch_rule1,adfetch_rule2` :

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