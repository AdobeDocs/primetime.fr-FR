---
title: Conditions requises pour l’utilisation de Primetime DRM Key Server
description: Conditions requises pour l’utilisation de Primetime DRM Key Server
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Introduction {#introduction}

Primetime DRM Key Server est un serveur de clés multi-locataires pour la diffusion clé à distance iOS et/ou Xbox 360. Si la diffusion de clés distantes est activée dans une stratégie pour iOS, un serveur de clés DRM Primetime doit être déployé afin d’activer la lecture de contenu sur les clients iOS. Primetime DRM Key Server est toujours requis pour Xbox 360.

## Conditions requises pour l’utilisation de Primetime DRM Key Server {#requirements-for-using-primetime-drm-key-server}

Les exigences minimales pour l’utilisation du serveur de clés DRM Primetime sont les suivantes :

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) ou plus tard. (Pour utiliser HSM sous Windows 64 bits, JRE 8 est requis)

  >[!NOTE]
  >
  >PKCS11 64 bits est désormais pris en charge dans OpenJDK 8 : [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131), et Oracle
* [Apache Tomcat 7](https://tomcat.apache.org)
* Informations d’identification émises par l’Adobe
* Informations d’identification émises par Microsoft (pour les clients Xbox 360)
