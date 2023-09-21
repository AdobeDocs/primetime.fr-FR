---
title: Conditions préalables
description: Conditions préalables
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Conditions préalables {#prerequisites}

Avant de grouper le contenu, un certificat Primetime DRM Packager est requis. Elle doit être demandée via le processus d’inscription de certificat DRM Primetime. Seul un certificat de package est requis (pas de serveur de licences ni de transport). Veuillez indiquer dans le courrier électronique de demande de certificat que la demande est pour un certificat à utiliser avec le service DRM.

[Guide d’inscription au certificat](../../digital-rights-management/certificate-enrollment-guide/about-certs.md)

Il existe deux niveaux de certificats d&#39;emballage : la production et le test. Le contenu empaqueté à l’aide de certificats TRIAL est destiné à un usage de développement uniquement et ne sera pas lu une fois le certificat expiré. Toutes les licences délivrées au contenu des essais auront une date d’expiration de stratégie codée en dur maximale égale à celle de la date d’expiration du certificat (si elle n’est pas définie dans la stratégie DRM).
