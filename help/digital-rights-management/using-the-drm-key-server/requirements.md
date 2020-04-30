---
seo-title: Configuration requise pour l’utilisation de Primetime DRM Key Server
title: Configuration requise pour l’utilisation de Primetime DRM Key Server
uuid: 769f9e10-7a3e-4a38-b30d-18181b666bb4
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Introduction {#introduction}

Primetime DRM Key Server est un serveur clé multi-locataire pour la diffusion clé iOS et/ou Xbox 360 distante. Si la Diffusion de clés distantes est activée dans une stratégie pour iOS, un serveur de clés DRM Primetime doit être déployé pour permettre la lecture de contenu sur les clients iOS. Primetime DRM Key Server est toujours requis pour Xbox 360.

## Configuration requise pour l’utilisation de Primetime DRM Key Server {#requirements-for-using-primetime-drm-key-server}

La configuration minimale requise pour utiliser le serveur de clés DRM Primetime est la suivante :

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) ou version ultérieure. (Pour utiliser HSM sous Windows 64 bits, JRE 8 est requis)

   >[!NOTE]
   >
   >PKCS11 64 bits est désormais pris en charge dans OpenJDK 8 : [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)et JDK Oracle : [https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559).

* [Apache Tomcat 7](https://tomcat.apache.org)
* Informations d’identification émises par Adobe
* Informations d&#39;identification émises par Microsoft (pour les clients Xbox 360)