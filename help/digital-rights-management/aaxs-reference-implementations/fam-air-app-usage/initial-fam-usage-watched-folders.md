---
title: Dossiers de contrôle
description: Dossiers de contrôle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Dossiers de contrôle {#watched-folders}

Vous pouvez utiliser des dossiers de contrôle pour regrouper automatiquement le contenu créé dans certains dossiers. Chaque dossier de contrôle peut être configuré avec différentes options de package. Pour tester les options de package avant de créer un dossier de contrôle, utilisez l’onglet Package Media .

Pour créer un dossier de contrôle, cliquez sur **[!UICONTROL Add New Watched Folder]** et renseignez les options de conditionnement. Voir [Package de fichiers multimédias](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md) pour une description de chaque option. Lorsque vous avez terminé, cliquez sur **[!UICONTROL Save Watched Folder Properties]**.

Lorsqu’un dossier de contrôle est enregistré, les options de package sont enregistrées dans *[Input Folder]* [!DNL \properties\watchfolder.properties]. Tout contenu ajouté au dossier d’entrée qui répond aux critères de sélection du fichier multimédia d’entrée est automatiquement mis en package et placé dans le dossier de sortie. Voir les préférences globales du dossier de contrôle dans la section [Préférences du module](../../aaxs-reference-implementations/fam-air-app-usage/initial-fam-setup-set-prefs/initial-fam-setup-pkg-prefs.md) pour configurer d’autres options du dossier de contrôle.

Pour modifier les paramètres de Watched Folder, sélectionnez le chemin d’entrée Watched Folder dans la liste située en haut de l’écran. Modifiez les paramètres et cliquez sur **[!UICONTROL Save Watched Folder Properties]**.

Pour supprimer un dossier de contrôle, sélectionnez le chemin d’entrée du dossier de contrôle dans la liste située en haut de l’écran, puis cliquez sur **[!UICONTROL Delete Watched Folder Properties]**.
