---
title: la critique de la politique de DRM
description: la critique de la politique de DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# la critique de la politique de DRM{#drm-policy-criticality}

Si vous prévoyez d’appliquer de nouvelles règles d’utilisation dans une stratégie DRM et si vous prévoyez d’utiliser cette stratégie DRM dans du contenu qui a été compilé pour des serveurs de licences plus anciens (et qui par conséquent n’interprète pas correctement les nouvelles règles d’utilisation), vous devrez peut-être spécifier le comportement que les anciens serveurs de licences doivent adopter. Par défaut, la criticité de la politique DRM est définie sur `true`.

Ce paramètre indique que le serveur de licences doit traiter toutes les parties de la stratégie DRM avant de pouvoir générer une licence qui utilise la stratégie DRM spécifiée. Si la critique de la politique DRM est définie sur `false`, un ancien serveur de licences peut ignorer les parties de la stratégie DRM qu’il ne peut pas interpréter correctement. Par conséquent, les licences générées par le serveur n’incluent aucune nouvelle règle d’utilisation.

Les serveurs DRM Primetime prenant en charge la version 2.0.2 ou ultérieure du SDK acceptent le paramètre de criticité de la stratégie DRM.
