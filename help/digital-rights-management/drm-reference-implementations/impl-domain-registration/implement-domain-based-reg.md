---
seo-title: Mise en oeuvre de l'enregistrement des domaines basé sur l'identité
title: Mise en oeuvre de l'enregistrement des domaines basé sur l'identité
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Mettre en oeuvre l&#39;enregistrement de domaine basé sur l&#39;identité{#implement-identity-based-domain-registration}

1. Créez une stratégie DRM avec enregistrement obligatoire des domaines.
1. Spécifiez l’hôte et le port du serveur pour l’URL du serveur de domaine.

   Dans votre fichier [!DNL .properties], définissez :

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Rendez l’authentification obligatoire avec un nom d’utilisateur et un mot de passe.

   Dans votre fichier [!DNL .properties], définissez :

   ```
   policy.domain.anonymous=false 
   ```
