---
seo-title: Configuration du chemin d’accès et du chemin de classe
title: Configuration du chemin d’accès et du chemin de classe
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# Configuration du chemin d’accès et du chemin de classe{#configure-the-path-and-classpath}

Le [!DNL flashaccess.war] contient [!DNL jsafeWithNative.jar], qui est la bibliothèque Crypto-J. Cette dernière nécessite une bibliothèque native supplémentaire pour effectuer des opérations de chiffrement.

1. Ajouter la [!DNL jsafe] bibliothèque native à votre chemin.

   * **Linux /[!DNL libjsafe.so]-** Le répertoire contenant [!DNL libjsafe.so] doit se trouver sur le chemin d&#39;accès (les bibliothèques natives Crypto-J sont également disponibles pour d&#39;autres plateformes). Par exemple, définissez [!DNL libjsafe.so] sur `LD_LIBRARY_PATH`.

   * **Windows /[!DNL jsafe.dll]-** L&#39;homologue sur Windows à [!DNL libjsafe.so] est le bon [!DNL jsafe.dll].
   Ces bibliothèques sont disponibles dans le dossier de [!DNL thirdparty] bibliothèque.
1. Placez un des fichiers [!DNL adobe-flashaccess-certs] jar sur le chemin de classe.

       Ce fichier JAR n&#39;est pas inclus dans le fichier WAR; vous devez l’ajouter explicitement au chemin de classe.
   
   * Serveurs de développement - Ne doit utiliser que [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Serveurs de production - Ne doit utiliser que [!DNL adobe-flashaccess- certs.jar]

La distribution comprend un [!DNL shared] dossier qui inclut le fichier jar ainsi qu’un [!DNL AdobeInitial.properties] fichier préconfiguré. Adobe recommande d’ajouter ces éléments au fichier `common.loader` via le [!DNL catalina.properties] . Par exemple :

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


