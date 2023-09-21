---
title: Scrambler de mot de passe
description: Scrambler de mot de passe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Scrambler de mot de passe {#password-scrambler}

L’utilitaire Scrambler de mot de passe chiffre un mot de passe afin qu’il puisse être utilisé dans les fichiers de configuration Adobe Access Server for Protected Streaming. Pour exécuter le scrambler, exécutez la commande :

```
Scrambler.bat password 
```

ou la commande :

```
java -jar libs/flashaccess-scrambler.jar password  
```

L’utilitaire génère le message suivant :

```
Encrypted password: scrambled-password 
```

Tous les mots de passe spécifiés dans flashaccess-global.xml et flashaccess-tenant.xml doivent être chiffrés.

>[!NOTE]
>
>L’utilitaire Scrambler de mot de passe d’Adobe Access Server for Protected Streaming n’est pas interchangeable avec le scrambler fourni avec le serveur de licence de mise en oeuvre de référence.
