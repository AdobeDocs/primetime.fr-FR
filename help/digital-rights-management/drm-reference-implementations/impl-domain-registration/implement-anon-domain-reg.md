---
title: Mise en oeuvre de l’enregistrement de domaine anonyme
description: Mise en oeuvre de l’enregistrement de domaine anonyme
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# Mise en oeuvre de l’enregistrement de domaine anonyme{#implement-anonymous-domain-registration}

1. Créez une stratégie DRM qui spécifie que l’enregistrement de domaine est requis.
1. Spécifiez l’URL du serveur de domaine comme suit :

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Rendre l’authentification anonyme obligatoire.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.anonymous=true 
   ```
