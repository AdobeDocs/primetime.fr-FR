---
description: 'null'
seo-description: 'null'
seo-title: Préparation des mots de passe à l’aide d’Ant
title: Préparation des mots de passe à l’aide d’Ant
uuid: 9419ab0d-b448-4881-9d26-35c00f0b13bc
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Préparation des mots de passe à l’aide d’Ant{#prepare-passwords-using-ant}

Utilisez Ant pour chiffrer votre mot de passe :

1. Accédez à `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Définissez la `sdkdir` propriété dans [!DNL build-refimpl.xml] pour pointer vers le répertoire qui inclut le SDK Java DRM Primetime.
1. Exécutez la commande suivante :

   ```
   ant -f build-refimpl.xml
   ```

