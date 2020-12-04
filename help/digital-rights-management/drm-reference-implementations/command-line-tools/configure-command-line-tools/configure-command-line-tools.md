---
seo-title: Configuration et exécution des outils de ligne de commande
title: Configuration et exécution des outils de ligne de commande
uuid: b65f8621-54fa-4927-b2f4-d2fd60350fc1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
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