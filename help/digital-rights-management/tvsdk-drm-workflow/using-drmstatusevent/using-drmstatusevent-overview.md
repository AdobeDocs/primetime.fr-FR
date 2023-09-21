---
title: Utilisation de la classe DRMStatusEvent - Aperçu
description: Utilisation de la classe DRMStatusEvent - Aperçu
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Présentation {#using-the-drmstatusevent-class-overview}

A `DRMStatusEvent` est distribué lorsque la lecture du contenu protégé par Primetime DRM commence correctement. (Le succès implique que la licence est vérifiée et que l’utilisateur est authentifié et autorisé à afficher le contenu).

La variable `DRMStatusEvent` contient des informations relatives à la licence, notamment si la licence peut être mise hors ligne ou si elle expire et que le contenu ne peut plus être affiché.
