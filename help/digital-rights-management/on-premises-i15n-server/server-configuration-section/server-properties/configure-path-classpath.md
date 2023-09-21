---
title: Configuration du chemin et du chemin d’accès aux classes
description: Configuration du chemin et du chemin d’accès aux classes
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Configuration du chemin et du chemin d’accès aux classes{#configure-the-path-and-classpath}

La variable [!DNL flashaccess.war] contains [!DNL jsafeWithNative.jar], qui est la bibliothèque Crypto-J. Cette dernière nécessite une bibliothèque native supplémentaire pour effectuer des opérations de cryptage.

1. Ajoutez le paramètre natif [!DNL jsafe] à votre chemin d’accès.

   * **Linux / [!DNL libjsafe.so] -** Le répertoire contenant [!DNL libjsafe.so] doit se trouver sur le chemin (les bibliothèques natives Crypto-J sont également disponibles pour d’autres plateformes). Par exemple, définissez [!DNL libjsafe.so] on `LD_LIBRARY_PATH`.

   * **Windows / [!DNL jsafe.dll] -** L’équivalent sous Windows pour [!DNL libjsafe.so] est approprié. [!DNL jsafe.dll].

   Ces bibliothèques sont à votre disposition dans la [!DNL thirdparty] dossier de bibliothèques.
1. Mets un des [!DNL adobe-flashaccess-certs] fichiers jar sur le chemin de classe.

       Ce fichier JAR n’est pas inclus dans le fichier WAR ; vous devez l’ajouter explicitement au chemin d’accès aux classes.
   
   * Serveurs de développement - Ne doit utiliser que [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Serveurs de production - Ne doit utiliser que [!DNL adobe-flashaccess- certs.jar]

La distribution comprend une [!DNL shared] dossier contenant à la fois le fichier jar et un fichier préconfiguré [!DNL AdobeInitial.properties] fichier . Adobe vous recommande d’ajouter ces éléments au `common.loader` via le [!DNL catalina.properties] fichier . Par exemple :

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```
