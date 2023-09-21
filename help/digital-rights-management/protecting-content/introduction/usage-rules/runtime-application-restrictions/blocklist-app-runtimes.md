---
title: Liste bloquée des exécutions d’application
description: Liste bloquée des exécutions d’application
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Liste bloquée des exécutions d’application {#blocklist-of-application-runtimes}

La liste bloquée des environnements d’exécution d’application spécifie la version du client Primetime ou du Runtime Flash qui ne peut pas accéder au contenu. Spécifiez le runtime, la plateforme et la version restreints (Flash Player, AIR ou iOS).

Exemple de cas d’utilisation : à l’instar de la liste bloquée client DRM Primetime, la dernière version du Flash Player, d’AIR ou d’iOS peut être spécifiée comme version minimale requise pour l’acquisition de licences et la lecture de contenu.

Vous pouvez identifier l’exécution de l’application par l’un des attributs pris en charge pour les versions client DRM Primetime, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Correspondance exacte | Identifie le nom de l’exécution de l’application. |
