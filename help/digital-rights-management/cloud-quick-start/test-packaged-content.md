---
title: Test du contenu empaqueté
description: Test du contenu empaqueté
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Test du contenu empaqueté {#test-the-packaged-content}

Vous devez vérifier que l’opération de conditionnement a réussi en utilisant le lecteur de bureau Adobe Primetime disponible publiquement (par Flash Player). Ce lecteur ne peut prendre en charge que le contenu HDS. Pour tester le contenu HLS, un lecteur compatible TVSDK avec navigateur Primetime est requis.

1. Hébergez votre contenu sur un serveur web.
1. Lancez le lecteur Primetime DRM (anciennement appelé Accès aux Adobes) à l’adresse https://drmtest2.adobe.com:8080/AccessPlayer/player.html.
1. Collez l’URL dans votre manifeste HDS ( [!DNL .f4m]) dans le champ de navigation du lecteur, puis cliquez sur l’icône **[!UICONTROL Play]** bouton .
