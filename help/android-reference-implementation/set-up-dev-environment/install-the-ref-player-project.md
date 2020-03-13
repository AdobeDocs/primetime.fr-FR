---
description: La référence Primetime TVSDK est une application Android conçue autour des structures TVSDK et AVE.
seo-description: La référence Primetime TVSDK est une application Android conçue autour des structures TVSDK et AVE.
seo-title: Création de l’implémentation de référence Primetime
title: Création de l’implémentation de référence Primetime
uuid: ab12660a-1563-49a4-82d9-1ab13f8a92be
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Création de l’implémentation de référence Primetime {#build-the-primetime-reference-implementation}

La référence Primetime TVSDK est une application Android conçue autour des structures TVSDK et AVE.

Configuration et génération du projet de référence Primetime dans Eclipse

1. Téléchargez le fichier compressé Android TVSDK et décompressez-le dans un répertoire dont vous vous souviendrez.
1. Lancez Eclipse.
1. Sélectionnez **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Sélectionnez **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Cliquez sur **[!UICONTROL Next]**.
1. Utilisez le **[!UICONTROL Browse]** bouton pour remplir le **[!UICONTROL Root Directory]** champ avec le répertoire sous [!DNL samples/PrimetimeReference/src] lequel vous avez décompressé le fichier zip Android TVSDK.
1. Sélectionnez les projets suivants à importer : **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**...
1. Cliquez sur **[!UICONTROL Finish]**.
1. Sélectionnez **[!UICONTROL Project]** > **[!UICONTROL Build Project]** pour créer le projet.

   Cette étape n’est pas nécessaire si le projet est configuré pour être généré automatiquement.
1. Si vous souhaitez inclure le projet de tests dans l’espace de travail, associez le projet de tests au projet PrimetimeReference :
   1. Répétez les étapes 3. à 6.
   1. Sélectionnez le projet suivant à importer : `PrimetimeReference\tests`.
   1. Cliquez sur **[!UICONTROL Finish]**.

      Le projet de tests dépend du projet CatalogActivity. Vous devez donc associer le projet de tests au projet CatalogActivity.
   1. Cliquez avec le bouton droit **[!UICONTROL tests]** de la souris, puis choisissez **[!UICONTROL Properties]**.
   1. Sélectionnez l’ **[!UICONTROL Projects]** onglet sous Chemin de version Java.
   1. Cliquez sur **[!UICONTROL Add...]**
   1. Sélectionnez CatalogActivity.
   1. Cliquez sur **[!UICONTROL OK]** pour ajouter le projet.
   1. Cliquez sur **[!UICONTROL OK]** pour quitter la page Propriétés.
   1. Sélectionnez **[!UICONTROL Project]** > **[!UICONTROL Build Project]** pour créer le projet.

      Cette étape n’est pas nécessaire si le projet est configuré pour être généré automatiquement.
