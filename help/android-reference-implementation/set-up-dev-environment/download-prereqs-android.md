---
seo-title: Téléchargement et configuration des logiciels prérequis
title: Téléchargement et configuration des logiciels prérequis
description: Le processus d'installation est simple. Si le JDK est déjà installé sur votre système, vous pouvez ignorer cette étape, mais sachez que votre JDK, Eclipse IDE et votre système d’exploitation doivent être compatibles.
seo-description: Le processus d'installation est simple. Si le JDK est déjà installé sur votre système, vous pouvez ignorer cette étape, mais sachez que votre JDK, Eclipse IDE et votre système d’exploitation doivent être compatibles.
uuid: ca29144f-8088-4c8d-93cf-aa59007da034
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Téléchargement et configuration du logiciel prérequis {#download-and-configure-prerequisite-software}

1. Téléchargez le JDK à l’adresse [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   Le processus d&#39;installation est simple. Si le JDK est déjà installé sur votre système, vous pouvez ignorer cette étape, mais sachez que votre JDK, Eclipse IDE et votre système d’exploitation doivent être compatibles.
1. Téléchargez l’Eclipse IDE for Java Developers à l’adresse [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   Après avoir décompressé le package, vous pouvez exécuter Eclipse directement. Il n&#39;y a pas de programme d&#39;installation.
1. Téléchargez le lot ADT du SDK Android à l’adresse [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   Ce lot comprend Eclipse. Si Eclipse est déjà installé sur votre système, vous pouvez télécharger les outils SDK de votre plate-forme à partir de la section [!UICONTROL Use An Existing IDE].

   Décompressez et installez-les à un emplacement dont vous vous souviendrez. Vous devrez vous y reporter ultérieurement.
1. Configurez le SDK Android.
   1. Ouvrez un terminal (sous Mac OS X) ou une invite de commande (sous Windows).
   1. Accédez au répertoire dans lequel vous avez téléchargé/décompressé le SDK Android.
   1. Accédez au dossier tools, qui contient un fichier nommé [!DNL android].
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

1. Configuration d’Eclipse.
   1. Début Eclipse.

      Sous Windows, si Eclipse ne début pas et si le problème signalé est qu’Eclipse ne peut pas trouver un fichier Java requis, essayez ce qui suit :

      * ajoutez `-vm C:\[path to your JDK bin]\javaw.exe` à votre fichier [!DNL eclipse.ini].
   1. Sélectionnez **[!UICONTROL Help]** > **[!UICONTROL Install New Software]**.
   1. Cliquez sur **[!UICONTROL Add...]**.
   1. Saisissez `Android` pour le nom.
   1. Entrez `https://dl-ssl.google.com/android/eclipse/` pour le lien **[!UICONTROL Work with]**.
   1. Cliquez sur **[!UICONTROL OK]**.

      Vous devriez voir une boîte de dialogue similaire à celle-ci :

      ![](assets/available_software.jpg)

   1. Sélectionnez les packages résultants (dans les outils de développement et les modules externes NDK) et cliquez sur **[!UICONTROL Next]**.

      Cela télécharge les outils de développement Android (ADT).
   1. Une fois le téléchargement terminé, redémarrez Eclipse.

   Le SDK Android est maintenant installé. 1. Configurez Eclipse de sorte qu’il puisse trouver le SDK Android et l’utiliser comme ressource.
   1. Ouvrez Eclipse.
   1. Sélectionnez **[!UICONTROL Window]** > **[!UICONTROL Preferences]** sous Windows ;  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** sous Mac OS X.
   1. Sélectionnez l&#39;onglet **[!UICONTROL Android]**.
   1. Accédez à l’emplacement du SDK Android.
   1. Cliquez sur **[!UICONTROL Apply]**.

      ![Résultat de l’étape](assets/ss2.jpg)


