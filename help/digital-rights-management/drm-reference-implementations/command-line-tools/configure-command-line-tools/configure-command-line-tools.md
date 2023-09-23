---
title: Configuration et exécution des outils de ligne de commande
description: Configuration et exécution des outils de ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Configuration et exécution des outils de ligne de commande {#configure-and-run-the-command-line-tools}

Les outils de ligne de commande sont associés à des propriétés pour lesquelles vous devez définir des valeurs dans [!DNL flashaccesstools.properties] *before* vous exécutez les outils. Certains outils de ligne de commande permettent également de spécifier des valeurs de propriété à partir de la ligne de commande. Les valeurs que vous spécifiez à partir de la ligne de commande sont prioritaires sur les valeurs fournies à partir de [!DNL flashaccesstools.properties].

Vous devez modifier les paramètres dans les sections suivantes de [!DNL flashaccesstools.properties] pour activer les outils de ligne de commande correspondants que vous avez l’intention d’utiliser :

* **Propriétés de Media Packager** - (pour [!DNL AdobePackager.jar])

* **Gestionnaire de listes de mise à jour de stratégie et propriétés du gestionnaire de listes de révocation** - (pour [!DNL AdobePolicyUpdateListManager.jar] et [!DNL AdobeRevocationListManager.jar])

* **Propriétés du gestionnaire de stratégies** - (pour [!DNL AdobePolicyManager.jar])

* **Propriétés du générateur de licences** - (pour [!DNL AdobeLicenseGenerator.jar])
