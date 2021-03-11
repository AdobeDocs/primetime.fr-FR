---
title: Présentation du déploiement des certificats
description: Présentation du déploiement des certificats
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Aperçu {#deploy-certificates-overview}

Pour ajouter des certificats aux fichiers de propriétés DRM Adobe Primetime, convertissez le fichier PKCS#7 en fichier PFX à l’aide de la clé privée et générez un fichier PEM ou DER.

* Lorsqu’une information d’identification (certificat et clé privée) est requise, les outils de ligne de commande DRM de Primetime et le module de HTTP Dynamic Streaming d’Adobe requièrent un fichier PFX. Le SDK, la mise en oeuvre des références et le serveur DRM Primetime pour la diffusion en flux continu protégée peuvent accepter un fichier PFX et utiliser également des informations d’identification stockées sur un HSM.
* Lorsque seul un certificat est requis, la plupart des composants DRM Primetime peuvent utiliser un fichier PEM, un fichier DER ou un certificat sur un HSM. Le Adobe HTTP Dynamic Streaming packager n’accepte que les fichiers DER pour les certificats.