---
title: Mise en oeuvre de l’enregistrement de domaine basé sur l’identité
description: Mise en oeuvre de l’enregistrement de domaine basé sur l’identité
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Mise en oeuvre de l’enregistrement de domaine basé sur l’identité{#implement-identity-based-domain-registration}

1. Créez une stratégie DRM avec l’enregistrement obligatoire du domaine.
1. Indiquez l’hôte et le port du serveur pour l’URL du serveur de domaine.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Rendre l’authentification avec un nom d’utilisateur et un mot de passe obligatoires.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.anonymous=false 
   ```
