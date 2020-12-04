---
seo-title: Chiffrer les mots de passe
title: Chiffrer les mots de passe
uuid: 94dc7fe9-fe40-4779-912a-d84b58e4ee36
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c
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

