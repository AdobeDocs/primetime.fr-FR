---
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
description: Préparation des mots de passe pour les fichiers de propriétés du serveur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Préparation des mots de passe pour les fichiers de propriétés du serveur {#preparing-passwords-for-the-server-properties-files}

Pour garantir la sécurité du mot de passe de vos informations d’identification, un outil est fourni pour chiffrer le mot de passe avant qu’il ne soit saisi dans la variable [!DNL flashaccess-refimpl.properties] ou [!DNL flashaccess-refimpl-packager.properties] fichier .

Pour exécuter l’outil à l’aide du script ANT fourni :

* Accédez à *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Assurez-vous que la variable `sdkdir` dans [!DNL build-refimpl.xml] pointe vers le répertoire contenant le SDK Adobe Access.
* Exécutez la commande suivante à l’aide de ANT :

  ```
      ant -f build-refimpl.xml
  ```

* Lorsque vous y êtes invité, saisissez le mot de passe de vos informations d’identification.

Pour exécuter l’outil à l’aide de Java :

* Accédez à *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* A partir de l&#39;invite de commande, saisissez la commande :

* Sous Windows :

  ```
  java -classpath path_to_adobe-flashaccess-sdk.jar;.  
  com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

* Sous Linux :

  ```
      java -classpath path_to_adobe-flashaccess-sdk.jar;.  
      com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

L’utilitaire génère le mot de passe chiffré, que vous devez copier dans le fichier .properties .

>[!NOTE]
>
>Les mots de passe codés à l’aide de l’utilitaire de recherche de mots de passe fourni avec l’implémentation de référence ne fonctionneront pas avec Adobe Access Server for Protected Streaming.
