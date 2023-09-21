---
title: Préparation des mots de passe à l’aide de Ant
description: Préparation des mots de passe à l’aide de Ant
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Préparation des mots de passe à l’aide de Ant{#prepare-passwords-using-ant}

Utilisez Ant pour chiffrer votre mot de passe :

1. Accédez à `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Définissez la variable `sdkdir` dans [!DNL build-refimpl.xml] pour pointer vers le répertoire contenant le SDK Java DRM Primetime.
1. Exécutez la commande suivante :

   ```
   ant -f build-refimpl.xml
   ```
