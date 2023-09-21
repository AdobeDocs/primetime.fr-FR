---
description: L’une des manières de coordonner l’application des licences et des stratégies consiste à intégrer ces fonctions dans un serveur de droits. Adobe fournit le serveur de droits de référence SEES avec lequel vous pouvez travailler pour créer votre propre serveur.
title: 'Exemple de serveur de référence : serveur de droits ExpressPlay (SEES)'
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Serveur de référence : exemple de serveur de droits ExpressPlay (SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

L’une des manières de coordonner l’application des licences et des stratégies consiste à intégrer ces fonctions dans un serveur de droits. Adobe fournit le serveur de droits de référence SEES avec lequel vous pouvez travailler pour créer votre propre serveur.

Le serveur de référence SEES illustre le service de droit ExpressPlay, présentant deux services : des droits de base basés sur le temps et des droits de liaison d’appareil.

Le SEES repose sur deux services ExpressPlay Fairplay :

1. Service de demande de jeton d’extraction
1. Service Expressplay Record Retriting

Le format d’URL de la requête de jeton ExpressPlay prend deux formes, l’une pour la production, l’autre pour l’environnement de test :

**Production**: accès<span></span>tps://fp-gen.{prod_domain}/hms/fp/token

**Test**: accès<span></span>tps://fp-gen.test.expressplay.com/hms/fp/token

Le format d’URL pour la récupération des enregistrements ExpressPlay prend deux formes, une pour la production, une pour l’environnement de test :

**Production**: accès<span></span>tps://api.{prod_domain}/cmiapi/getrecord/

**Test**: accès<span></span>tps://api.test.expressplay.com/cmiapi/getrecord/
