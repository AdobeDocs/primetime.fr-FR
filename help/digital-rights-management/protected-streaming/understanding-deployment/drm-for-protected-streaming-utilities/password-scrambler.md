---
description: L’utilitaire Password Scrambler chiffre un mot de passe pour le serveur Adobe Primetime DRM Server pour les fichiers de configuration de diffusion en flux continu protégé.
title: Défileur de mots de passe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Défileur de mot de passe {#password-scrambler}

L’utilitaire Password Scrambler chiffre un mot de passe pour le serveur Adobe Primetime DRM Server pour les fichiers de configuration de diffusion en flux continu protégé.

Pour exécuter le scrambler, tapez :

```
Scrambler.bat  
<i class="+ topic ph hi-d="" i "="">
  password 
</i class="+ topic>
```

ou

```
java -jar libs/flashaccess-scrambler.jar  
<i class="+ topic ph hi-d="" i "="">
  password  
</i class="+ topic>
```

L’utilitaire affiche le message suivant :

```
Encrypted password:  
<i class="+ topic ph hi-d="" i "="">
  scrambled-password 
</i class="+ topic>
```

Tous les mots de passe que vous avez spécifiés dans les fichiers [!DNL flashaccess-global.xml] et [!DNL flashaccess-tenant.xml] doivent être chiffrés.

>[!NOTE]
>
>L&#39;utilitaire Password Scrambler du serveur DRM Primetime pour la diffusion en flux continu protégée n&#39;est pas interchangeable avec le scrambler fourni avec le serveur de licence de mise en oeuvre de référence.