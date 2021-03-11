---
title: Configuration du chemin d’accès et du chemin de classe
description: Configuration du chemin d’accès et du chemin de classe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---


# Configuration du chemin et du chemin d’accès aux classes {#configure-the-path-and-classpath}

[!DNL flashaccess.war] contient [!DNL jsafeWithNative.jar], qui est la bibliothèque Crypto-J. Cette dernière requiert une bibliothèque native supplémentaire pour effectuer des opérations de chiffrement.

1. Ajoutez la bibliothèque [!DNL jsafe] native à votre chemin d’accès.

   * **Linux /  [!DNL libjsafe.so] -** Le répertoire contenant  [!DNL libjsafe.so] doit se trouver sur le chemin d&#39;accès (les bibliothèques natives Crypto-J sont également disponibles pour d&#39;autres plateformes). Par exemple, définissez [!DNL libjsafe.so] sur `LD_LIBRARY_PATH`.

   * **Windows /  [!DNL jsafe.dll] -** L&#39;homologue sur Windows à  [!DNL libjsafe.so] est le  [!DNL jsafe.dll]approprié.
   Ces bibliothèques sont disponibles dans le dossier de bibliothèque [!DNL thirdparty].
1. Placez un des fichiers jar [!DNL adobe-flashaccess-certs] sur le chemin de classe.

       Ce fichier JAR n&#39;est pas inclus dans le fichier WAR ; vous devez l&#39;ajouter explicitement au chemin de classe.
   
   * Serveurs de développement : ne doit utiliser que [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Serveurs de production - Ne doit utiliser que [!DNL adobe-flashaccess- certs.jar]

La distribution comprend un dossier [!DNL shared] qui comprend à la fois le fichier jar et un fichier [!DNL AdobeInitial.properties] préconfiguré. L&#39;Adobe vous recommande d&#39;ajouter ces éléments à `common.loader` via le fichier [!DNL catalina.properties]. Par exemple :

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


