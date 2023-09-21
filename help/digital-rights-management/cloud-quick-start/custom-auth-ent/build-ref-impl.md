---
title: Création de l’implémentation de référence BEES
description: Création de l’implémentation de référence BEES
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Création de l’implémentation de référence BEES {#build-the-bees-reference-implementation}

Vérifiez que vous utilisez Java 1.6.0_24 ou version ultérieure.
1. Renseignez les chemins vides nécessaires, tels que `tomcatdir` et `fasterxmldir` in [!DNL build-bees.xml]

   FasterXML/Jackson est inclus. Vous pouvez également le télécharger à partir de [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Mettre à jour les noms de fichiers jar réels dans [!DNL build.common.xml] si vous souhaitez utiliser une autre version des bibliothèques Jackson.
1. Exécutez la variable `all` cible de [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

La variable [!DNL bees.war] est créé dans la variable [!DNL bees-build/wars] dossier.
