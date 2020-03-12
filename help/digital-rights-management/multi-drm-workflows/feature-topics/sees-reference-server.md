---
description: Une manière de coordonner l'application des licences et des stratégies consiste à intégrer ces fonctions dans un serveur de droits. Adobe fournit le serveur de droits de référence SEES avec lequel vous pouvez travailler pour créer votre propre serveur.
seo-description: Une manière de coordonner l'application des licences et des stratégies consiste à intégrer ces fonctions dans un serveur de droits. Adobe fournit le serveur de droits de référence SEES avec lequel vous pouvez travailler pour créer votre propre serveur.
seo-title: Exemple de serveur de référence ExpressPlay Entitlement Server (SEES)
title: Exemple de serveur de référence ExpressPlay Entitlement Server (SEES)
uuid: 99e42f76-7730-42fc-a9a9-f6396ac12c02
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Serveur de référence : Exemple de serveur de droits ExpressPlay (SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

Une manière de coordonner l&#39;application des licences et des stratégies consiste à intégrer ces fonctions dans un serveur de droits. Adobe fournit le serveur de droits de référence SEES avec lequel vous pouvez travailler pour créer votre propre serveur.

Le serveur de référence SEES présente le service de droits ExpressPlay, avec deux services : droits de base basés sur le temps et droits de liaison de périphérique.

Le SEES est construit sur deux services Fairplay ExpressPlay :

1. Service de demande de jeton Expressplay
1. Service Expressplay Record Retriting

Le format d’URL de la demande de jeton ExpressPlay se présente sous deux formes : une pour la production, une pour le  de test  :

**Production**:<span></span>https://fp-gen.{prod_domain}/hms/fp/token

**Test**:<span></span>https://fp-gen.test.expressplay.com/hms/fp/token

Le format d’URL pour la récupération des enregistrements ExpressPlay prend deux formes, une pour la production, une pour le  de test  :

**Production**:<span></span>https://api.{prod_domain}/cmiapi/getrecord/

**Test**:<span></span>https://api.test.expressplay.com/cmiapi/getrecord/
