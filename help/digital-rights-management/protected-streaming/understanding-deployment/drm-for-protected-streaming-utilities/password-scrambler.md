---
description: L’utilitaire Password Scrambler crypte un mot de passe pour le serveur Adobe Primetime DRM pour les fichiers de configuration de diffusion en continu protégée.
title: Délimiteur de mot de passe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Délimiteur de mot de passe {#password-scrambler}

L’utilitaire Password Scrambler crypte un mot de passe pour le serveur Adobe Primetime DRM pour les fichiers de configuration de diffusion en continu protégée.

Pour exécuter le scrambler, saisissez :

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

Tous les mots de passe que vous avez spécifiés dans la variable [!DNL flashaccess-global.xml] et [!DNL flashaccess-tenant.xml] Les fichiers doivent être cryptés.

>[!NOTE]
>
>L’utilitaire Password Scrambler du serveur Primetime DRM for Protected Streaming n’est pas interchangeable avec le scrambler fourni avec le serveur de licence de mise en oeuvre de référence.
