---
seo-title: Mise en oeuvre de l’enregistrement de domaine basé sur l’identité
title: Mise en oeuvre de l’enregistrement de domaine basé sur l’identité
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Mise en oeuvre de l’enregistrement de domaine basé sur l’identité{#implement-identity-based-domain-registration}

1. Créez une stratégie DRM avec enregistrement de domaine obligatoire.
1. Spécifiez l’hôte et le port du serveur pour l’URL du serveur de domaine.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Rendre l’authentification obligatoire avec un nom d’utilisateur et un mot de passe.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.anonymous=false 
   ```
