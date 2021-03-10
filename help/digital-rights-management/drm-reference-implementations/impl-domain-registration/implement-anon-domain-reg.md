---
title: Mise en oeuvre de l’enregistrement de domaine anonyme
description: Mise en oeuvre de l’enregistrement de domaine anonyme
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
