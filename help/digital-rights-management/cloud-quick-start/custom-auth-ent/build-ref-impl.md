---
seo-title: Création de l’implémentation de référence BEES
title: Création de l’implémentation de référence BEES
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Création de l’implémentation de référence BEES {#build-the-bees-reference-implementation}

Vérifiez que vous utilisez Java 1.6.0_24 ou version ultérieure.
1. Renseignez les chemins vides nécessaires, tels que `tomcatdir` et `fasterxmldir` dans [!DNL build-bees.xml]

   FastXML/Jackson est inclus. Vous pouvez également le télécharger à partir de [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Mettez à jour les noms de fichiers jar réels dans [!DNL build.common.xml] si vous souhaitez utiliser une autre version des bibliothèques Jackson.
1. Exécutez le `all` de [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

Le [!DNL bees.war] sera créé dans le [!DNL bees-build/wars] dossier.