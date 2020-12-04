---
seo-title: Préparation des mots de passe pour les fichiers de propriétés du serveur
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
uuid: 2d876eb0-b1a5-4c30-ae96-0a22f6a03910
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Préparation des mots de passe pour les fichiers de propriétés du serveur {#preparing-passwords-for-the-server-properties-files}

Pour garantir la sécurité du mot de passe de vos informations d’identification, un outil est fourni pour chiffrer le mot de passe avant qu’il ne soit entré dans le fichier [!DNL flashaccess-refimpl.properties] ou [!DNL flashaccess-refimpl-packager.properties].

Pour exécuter l&#39;outil à l&#39;aide du script ANT fourni :

* Accéder à *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Assurez-vous que la propriété `sdkdir` de [!DNL build-refimpl.xml] pointe vers le répertoire contenant le SDK d&#39;accès à l&#39;Adobe.
* Exécutez la commande suivante à l’aide d’ANT :

   ```
       ant -f build-refimpl.xml
   ```

* Lorsque vous y êtes invité, saisissez le mot de passe de vos informations d’identification.

Pour exécuter l’outil à l’aide de Java :

* Accéder à *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* Dans l&#39;invite de commande, saisissez la commande suivante :

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
