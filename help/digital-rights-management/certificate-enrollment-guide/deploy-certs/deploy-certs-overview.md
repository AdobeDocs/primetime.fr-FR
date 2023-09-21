---
title: Présentation du déploiement des certificats
description: Présentation du déploiement des certificats
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Présentation {#deploy-certificates-overview}

Pour ajouter des certificats aux fichiers de propriétés DRM Adobe Primetime, convertissez le fichier PKCS#7 en fichier PFX à l’aide de la clé privée et générez un fichier PEM ou DER.

* Lorsqu’un identifiant (certificat et clé privée) est requis, les outils de ligne de commande Primetime DRM et le service de package de HTTP Dynamic Streaming d’Adobe requièrent un fichier PFX. Le SDK, la mise en oeuvre de référence et le serveur DRM Primetime pour la diffusion protégée peuvent accepter un fichier PFX et utiliser également des informations d’identification stockées sur un HSM.
* Lorsque seul un certificat est requis, la plupart des composants DRM Primetime peuvent utiliser un fichier PEM, un fichier DER ou un certificat sur un HSM. Le Adobe HTTP Dynamic Streaming packager accepte uniquement les fichiers DER pour les certificats.
