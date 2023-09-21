---
description: La référence Primetime TVSDK est une application Android qui repose sur les structures TVSDK et AVE.
title: Création de l’implémentation de référence Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Création de l’implémentation de référence Primetime {#build-the-primetime-reference-implementation}

La référence Primetime TVSDK est une application Android qui repose sur les structures TVSDK et AVE.

Pour configurer et créer le projet Primetime Reference dans Eclipse :

1. Téléchargez le fichier zip Android TVSDK et décompressez-le dans un répertoire à un emplacement que vous mémoriserez.
1. Lancez Eclipse.
1. Sélectionner **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Sélectionner **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Cliquez sur **[!UICONTROL Next]**.
1. Utilisez la variable **[!UICONTROL Browse]** pour renseigner la variable **[!UICONTROL Root Directory]** avec le répertoire sous [!DNL samples/PrimetimeReference/src] dans lequel vous avez décompressé le fichier zip Android TVSDK.
1. Sélectionnez les projets suivants à importer : **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. Cliquez sur **[!UICONTROL Finish]**.
1. Sélectionner  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** pour créer le projet.

   Cette étape n’est pas nécessaire si le projet est configuré pour être automatiquement créé.
1. Si vous souhaitez inclure le projet tests dans l’espace de travail, associez le projet tests au projet PrimetimeReference :
   1. Répétez les étapes 3. à 6.
   1. Sélectionnez le projet suivant à importer : `PrimetimeReference\tests`.
   1. Cliquez sur **[!UICONTROL Finish]**.

      Le projet Tests dépend du projet CatalogActivity. Vous devez donc associer le projet Tests au projet CatalogActivity.
   1. Clic droit **[!UICONTROL tests]** et choisissez **[!UICONTROL Properties]**.
   1. Sélectionnez la variable **[!UICONTROL Projects]** sous Chemin de création Java.
   1. Cliquez sur **[!UICONTROL Add...]**
   1. Sélectionnez CatalogActivity.
   1. Cliquez sur **[!UICONTROL OK]** pour ajouter le projet.
   1. Cliquez sur **[!UICONTROL OK]** pour quitter la page Propriétés.
   1. Sélectionner  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** pour créer le projet.

      Cette étape n’est pas nécessaire si le projet est configuré pour être automatiquement créé.
