---
seo-title: Mise en oeuvre de l’enregistrement de domaine anonyme
title: Mise en oeuvre de l’enregistrement de domaine anonyme
uuid: 330d32fd-8c23-40f9-949b-635e5a9acc86
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Mise en oeuvre de l’enregistrement de domaine anonyme{#implement-anonymous-domain-registration}

1. Créez une stratégie DRM spécifiant que l’enregistrement de domaine est obligatoire.
1. Spécifiez l’URL du serveur de domaine comme suit :

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Rendre l’authentification anonyme obligatoire.

   Dans votre [!DNL .properties] fichier, définissez :

   ```
   policy.domain.anonymous=true 
   ```
