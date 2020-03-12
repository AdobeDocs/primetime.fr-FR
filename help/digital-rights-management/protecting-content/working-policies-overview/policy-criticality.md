---
seo-title: La politique de la DRM
title: La politique de la DRM
uuid: ddc03142-7acb-4a9f-a367-e34cfc5e78ba
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# La politique de la DRM{#drm-policy-criticality}

Si vous prévoyez d’appliquer de nouvelles règles d’utilisation dans une stratégie DRM et si vous prévoyez d’utiliser cette stratégie DRM dans le contenu qui a été inclus pour les anciens serveurs de licences (et qui par conséquent n’interprète pas correctement les nouvelles règles d’utilisation), vous devrez peut-être spécifier le comportement des anciens serveurs de licences. Par défaut, la valeur de la critique de la politique DRM est définie sur `true`.

Ce paramètre indique que le serveur de licences doit traiter toutes les parties de la stratégie DRM avant de pouvoir générer une licence qui utilise la stratégie DRM spécifiée. Si la valeur de la stratégie DRM est définie sur `false`, un ancien serveur de licences peut ignorer les parties de la stratégie DRM qu’il ne peut pas interpréter correctement. Par conséquent, les licences générées par le serveur n’incluent aucune nouvelle règle d’utilisation.

Les serveurs DRM Primetime qui prennent en charge la version 2.0.2 du SDK ou une version ultérieure acceptent le paramètre de valeur de la stratégie DRM.
