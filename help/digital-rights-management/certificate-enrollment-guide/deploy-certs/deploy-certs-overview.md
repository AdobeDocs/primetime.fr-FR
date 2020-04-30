---
seo-title: Présentation du déploiement des certificats
title: Présentation du déploiement des certificats
uuid: e6413f9f-69a5-4881-bb13-47a80cf32a48
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Présentation {#deploy-certificates-overview}

Pour ajouter des certificats aux fichiers de propriétés DRM d’Adobe Primetime, convertissez le fichier PKCS#7 en fichier PFX à l’aide de la clé privée et générez un fichier PEM ou DER.

* Lorsqu’une information d’identification (certificat et clé privée) est requise, les outils de ligne de commande DRM Primetime et le module de diffusion en flux continu dynamique HTTP Adobe nécessitent un fichier PFX. Le SDK, la mise en oeuvre des références et le serveur DRM Primetime pour la diffusion en flux continu protégée peuvent accepter un fichier PFX et utiliser également des informations d’identification stockées sur un HSM.
* Lorsque seul un certificat est requis, la plupart des composants DRM Primetime peuvent utiliser un fichier PEM, un fichier DER ou un certificat sur un HSM. Adobe HTTP Dynamic Streaming Packager n’accepte que les fichiers DER pour les certificats.