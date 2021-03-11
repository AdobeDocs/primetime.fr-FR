---
title: Préparation des mots de passe à l’aide d’Ant
description: Préparation des mots de passe à l’aide d’Ant
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---


# Préparation des mots de passe à l’aide d’Ant{#prepare-passwords-using-ant}

Utilisez Ant pour chiffrer votre mot de passe :

1. Accédez à `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Définissez la propriété `sdkdir` dans [!DNL build-refimpl.xml] pour pointer vers le répertoire qui inclut le SDK Java DRM Primetime.
1. Exécutez la commande suivante :

   ```
   ant -f build-refimpl.xml
   ```

