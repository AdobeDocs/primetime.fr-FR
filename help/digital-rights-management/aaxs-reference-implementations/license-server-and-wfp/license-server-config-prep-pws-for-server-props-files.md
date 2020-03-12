---
seo-title: Préparation des mots de passe pour les fichiers de propriétés du serveur
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
uuid: 2d876eb0-b1a5-4c30-ae96-0a22f6a03910
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Préparation des mots de passe pour les fichiers de propriétés du serveur {#preparing-passwords-for-the-server-properties-files}

Pour garantir la sécurité du mot de passe de vos informations d’identification, un outil est fourni pour chiffrer le mot de passe avant qu’il ne soit entré dans le [!DNL flashaccess-refimpl.properties] fichier ou [!DNL flashaccess-refimpl-packager.properties] le fichier.

Pour exécuter l’outil à l’aide du script ANT fourni :

* Aller à *`<Reference Implementation Server Path>`*[!DNL \refimpl]

* Assurez-vous que la `sdkdir` propriété dans [!DNL build-refimpl.xml] pointe vers le répertoire contenant le SDK Adobe Access.
* Exécutez la commande suivante à l’aide d’ANT :

   ```
       ant -f build-refimpl.xml
   ```

* Lorsque vous y êtes invité, saisissez le mot de passe de vos informations d’identification.

Pour exécuter l’outil à l’aide de Java :

* Aller à *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* Dans l’invite de commande, saisissez la commande suivante :

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

L’utilitaire génère le mot de passe chiffré que vous devez copier dans le fichier .properties.

>[!NOTE]
>
>Les mots de passe codés à l’aide de l’utilitaire de brouillage de mot de passe fourni avec l’implémentation des références ne fonctionneront pas avec Adobe Access Server for Protected Streaming.
