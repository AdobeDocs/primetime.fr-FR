---
description: L’utilitaire Password Scrambler chiffre un mot de passe pour le serveur DRM d’Adobe Primetime pour les fichiers de configuration de diffusion en flux continu protégé.
seo-description: L’utilitaire Password Scrambler chiffre un mot de passe pour le serveur DRM d’Adobe Primetime pour les fichiers de configuration de diffusion en flux continu protégé.
seo-title: Défileur de mots de passe
title: Défileur de mots de passe
uuid: 56df0f49-f3fd-464d-b4ba-25e1b497158a
translation-type: tm+mt
source-git-commit: 105dedcfe47a5f454a067e66a95827e638290742

---


# Défileur de mots de passe {#password-scrambler}

L’utilitaire Password Scrambler chiffre un mot de passe pour le serveur DRM d’Adobe Primetime pour les fichiers de configuration de diffusion en flux continu protégé.

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

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L&#39;utilitaire Password Scrambler du serveur DRM Primetime pour la diffusion en flux continu protégée n&#39;est pas interchangeable avec le scrambler fourni avec le serveur de licence de mise en oeuvre de référence.