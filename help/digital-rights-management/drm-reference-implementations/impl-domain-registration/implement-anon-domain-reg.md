---
seo-title: Mise en oeuvre de l’enregistrement de domaine anonyme
title: Mise en oeuvre de l’enregistrement de domaine anonyme
uuid: 330d32fd-8c23-40f9-949b-635e5a9acc86
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Mettre en oeuvre l&#39;enregistrement de domaine anonyme{#implement-anonymous-domain-registration}

1. Créez une stratégie DRM qui spécifie que l&#39;enregistrement de domaine est requis.
1. Spécifiez l’URL du serveur de domaine en tant que :

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Rendre l’authentification anonyme obligatoire.

   Dans votre fichier [!DNL .properties], définissez :

   ```
   policy.domain.anonymous=true 
   ```
