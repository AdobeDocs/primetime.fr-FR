---
title: Téléchargement et configuration d’un logiciel prérequis
description: Le processus d’installation est simple. Si le JDK est déjà installé sur votre système, vous pouvez ignorer cette étape, mais sachez que votre JDK, Eclipse IDE et votre système d’exploitation doivent être compatibles.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Téléchargement et configuration d’un logiciel prérequis {#download-and-configure-prerequisite-software}

1. Téléchargez le JDK à partir de [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   Le processus d’installation est simple. Si le JDK est déjà installé sur votre système, vous pouvez ignorer cette étape, mais sachez que votre JDK, Eclipse IDE et votre système d’exploitation doivent être compatibles.
1. Téléchargez l’IDE Eclipse pour les développeurs Java depuis [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   Après avoir décompressé le package, vous pouvez exécuter Eclipse directement. Il n’y a pas de programme d’installation.
1. Téléchargez le bundle ADT du SDK Android à partir de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   Ce lot comprend Eclipse. Si Eclipse est déjà installé sur votre système, vous pouvez télécharger les outils de SDK pour votre plateforme à partir de la page [!UICONTROL Use An Existing IDE] .

   Décompressez et installez-les à un emplacement dont vous vous souviendrez. Vous devrez vous y référer ultérieurement.
1. Configurez le SDK Android.
   1. Ouvrez un terminal (sous Mac OS X) ou une invite de commande (sous Windows).
   1. Accédez au répertoire dans lequel vous avez téléchargé/décompressé le SDK Android.
   1. Accédez au dossier des outils, qui contient un fichier nommé [!DNL android].
   1. Exécutez les commandes suivantes :

      * Pour Mac OS X/Unix :

        ```
        chmod +x android 
        android update sdk --no-ui
        ```

      * Pour Windows :

        ```
        android update sdk --no-ui
        ```

        Ce processus prend du temps.

1. Configurez Eclipse.
   1. Démarrez Eclipse.

      Sous Windows, si Eclipse ne démarre pas et que le problème signalé est qu’Eclipse ne parvient pas à trouver un fichier Java requis, essayez les méthodes suivantes :

      * add `-vm C:\[path to your JDK bin]\javaw.exe` à votre [!DNL eclipse.ini] fichier .
   1. Sélectionner  **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. Cliquez sur **[!UICONTROL Add...]**.
   1. Entrée `Android` pour le nom.
   1. Entrée `https://dl-ssl.google.com/android/eclipse/` pour le **[!UICONTROL Work with]** lien.
   1. Cliquez sur **[!UICONTROL OK]**.

      Vous devriez voir une boîte de dialogue similaire à celle-ci :

      ![](assets/available_software.jpg)

   1. Sélectionnez les modules résultants (ceux des outils de développement et des modules externes NDK) et cliquez sur **[!UICONTROL Next]**.

      Cela télécharge les outils de développement Android (ADT).
   1. Une fois le téléchargement terminé, redémarrez Eclipse.

   Le SDK Android est maintenant installé. 1. Configurez Eclipse pour qu’il puisse trouver le SDK Android et l’utiliser comme ressource.
   1. Ouvrez Eclipse.
   1. Sélectionner  **[!UICONTROL Window]** > **[!UICONTROL Preferences]** sous Windows ;  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** sous Mac OS X.
   1. Sélectionnez la variable **[!UICONTROL Android]** .
   1. Accédez à l’emplacement du SDK Android.
   1. Cliquez sur **[!UICONTROL Apply]**.

      ![Résultat de l’étape](assets/ss2.jpg)
