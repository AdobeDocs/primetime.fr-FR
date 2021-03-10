---
title: Chiffrer les mots de passe
description: Chiffrer les mots de passe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---


# Chiffrer les mots de passe {#encrypt-passwords}

Les fichiers de propriétés comportent plusieurs valeurs de mot de passe que vous ne devez pas saisir en texte brut. Chiffrez ces valeurs à l’aide de la commande suivante :

`java -jar adobe-flashaccess-i15n-setup.jar password`

Cette commande génère un mot de passe chiffré, que vous utiliserez ensuite dans les fichiers de propriétés.

>[!NOTE]
>Il ne s&#39;agit pas de l&#39;utilitaire utilisé pour chiffrer les mots de passe du serveur de licences.

