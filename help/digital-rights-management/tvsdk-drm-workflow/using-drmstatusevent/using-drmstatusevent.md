---
title: Utilisation de la classe DRMStatusEvent - Aperçu
description: Utilisation de la classe DRMStatusEvent - Aperçu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Utilisation de la classe DRMStatusEvent - Aperçu {#using-the-drmstatusevent-class-overview}

A `DRMStatusEvent` est distribué lorsque la lecture du contenu protégé par Primetime DRM commence correctement. (Le succès implique que la licence est vérifiée et que l’utilisateur est authentifié et autorisé à afficher le contenu).

La variable `DRMStatusEvent` contient des informations relatives à la licence, notamment si la licence peut être mise hors ligne ou si elle expire et que le contenu ne peut plus être affiché.
