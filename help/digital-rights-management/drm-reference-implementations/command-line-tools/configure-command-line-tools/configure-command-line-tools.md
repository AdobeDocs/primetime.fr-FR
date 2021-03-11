---
title: Configuration et exécution des outils de ligne de commande
description: Configuration et exécution des outils de ligne de commande
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# Configurer et exécuter les outils de ligne de commande {#configure-and-run-the-command-line-tools}

Les outils de ligne de commande sont associés à des propriétés pour lesquelles vous devez définir des valeurs dans [!DNL flashaccesstools.properties] *avant d&#39;exécuter les outils.* Certains outils de ligne de commande permettent également de spécifier des valeurs de propriété à partir de la ligne de commande. Les valeurs que vous spécifiez à partir de la ligne de commande sont prioritaires sur les valeurs fournies à partir de [!DNL flashaccesstools.properties].

Vous devez modifier les paramètres dans les sections suivantes de [!DNL flashaccesstools.properties] pour activer les outils de ligne de commande correspondants que vous envisagez d&#39;utiliser :

* **Propriétés**  de Media Packager - (pour  [!DNL AdobePackager.jar])

* **Propriétés**  du Gestionnaire de Listes de mise à jour des stratégies et du Gestionnaire de Listes de révocation - (pour  [!DNL AdobePolicyUpdateListManager.jar] et  [!DNL AdobeRevocationListManager.jar]pour)

* **Propriétés**  du gestionnaire de stratégies - (pour  [!DNL AdobePolicyManager.jar])

* **Propriétés**  du générateur de licences - (pour  [!DNL AdobeLicenseGenerator.jar])