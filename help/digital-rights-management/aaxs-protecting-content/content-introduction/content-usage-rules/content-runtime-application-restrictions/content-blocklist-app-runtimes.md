---
title: Liste bloquée des environnements d’exécution d’application empêchés d’accéder au contenu protégé
description: Liste bloquée des environnements d’exécution d’application empêchés d’accéder au contenu protégé
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Liste bloquée des environnements d’exécution d’application empêchés d’accéder au contenu protégé {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

Indique la version de Primetime ou Flash Runtime qui ne peut pas accéder au contenu. Spécifiez le runtime, la plateforme et la version restreints (Flash Player, AIR ou iOS).

Exemple de cas d’utilisation : à l’instar de la liste bloquée client DRM, la dernière version du Flash Player, d’AIR ou d’iOS peut être spécifiée comme version minimale requise pour l’acquisition de licences et la lecture de contenu.

L’exécution de l’application peut être identifiée par l’un des attributs pris en charge pour les versions client DRM, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Correspondance exacte | Identifie le nom de l’exécution de l’application. |
