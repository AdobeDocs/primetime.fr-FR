---
title: Installation des outils de ligne de commande
description: Installation des outils de ligne de commande
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# Installer les outils de ligne de commande {#install-the-command-line-tools}

1. Copiez le contenu du répertoire [DRM SDK DVD]\Reference Implementation\Command Line Tools\ dans un répertoire de travail de votre système.

   [!DNL .../Command Line Tools/] contents :

   * [!DNL flashaccesstools.properties] - Fichier de configuration par défaut pour les outils de ligne de commande.
   * [!DNL libs/] - Contient les fichiers JAR des outils de ligne de commande
   * [!DNL samples/] - Contient le script de build ant (  [!DNL build-samples.xml]) et les fichiers source Java.

      >[!NOTE]
      >
      >Les fichiers source Java montrent comment utiliser les API SDK DRM de Primetime. Pour créer et exécuter les exemples, exécutez le script Ant [!DNL build-samples.xml] dans [!DNL samples/].