---
title: Emission de licences pour la diffusion à clé distante vers les clients iOS (nécessite Adobe Primetime)
description: Emission de licences pour la diffusion à clé distante vers les clients iOS (nécessite Adobe Primetime)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Emission de licences pour la diffusion à clé distante vers les clients iOS (nécessite Adobe Primetime){#issuing-licenses-for-remote-key-delivery-to-ios-clients-requires-adobe-primetime}

Si vous souhaitez émettre des licences pour du contenu qui nécessite une diffusion de clé à distance pour les appareils iOS, vous devez spécifier le certificat du serveur de licences du serveur de clés dans `HandlerConfiguration.setKeyServerCertificate()`.
