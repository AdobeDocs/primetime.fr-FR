---
seo-title: Paramètre de mot de passe
title: Paramètre de mot de passe
uuid: e488babc-cd50-41b9-acb8-490e8e42e8bc
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# Paramètre de mot de passe {#password-scrambler}

L’utilitaire Password Scrambler crypte un mot de passe afin qu’il puisse être utilisé dans les fichiers de configuration Adobe Access Server for Protected Streaming. Pour exécuter le scrambler, exécutez la commande :

```
Scrambler.bat password 
```

ou la commande :

```
java -jar libs/flashaccess-scrambler.jar password  
```

L&#39;utilitaire affiche le message suivant :

```
Encrypted password: scrambled-password 
```

Tous les mots de passe spécifiés dans flashaccess-global.xml et flashaccess-locataire.xml doivent être chiffrés.

>[!NOTE]
>
>L’utilitaire Password Scrambler d’Adobe Access Server for Protected Streaming n’est pas interchangeable avec le scrambler fourni avec le serveur de licence de mise en oeuvre de référence.

