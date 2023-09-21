---
title: Chiffrer les mots de passe
description: Chiffrer les mots de passe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---

# Chiffrer les mots de passe{#encrypt-passwords}

Les fichiers de propriétés comprennent plusieurs valeurs de mot de passe que vous ne devez pas saisir en texte brut. Chiffrez ces valeurs à l’aide de la commande suivante :

`java -jar adobe-flashaccess-i15n-setup.jar password`

Cette commande génère un mot de passe chiffré que vous utilisez ensuite dans les fichiers de propriétés.

>[!NOTE]
>Il ne s’agit pas de l’utilitaire utilisé pour chiffrer les mots de passe du serveur de licences.
