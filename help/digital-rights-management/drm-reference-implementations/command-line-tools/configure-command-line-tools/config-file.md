---
description: 'null'
seo-description: 'null'
seo-title: A propos des fichiers de configuration des outils de ligne de commande
title: A propos des fichiers de configuration des outils de ligne de commande
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# A propos des fichiers de configuration des outils de ligne de commande{#about-command-line-tools-configuration-files}

Les outils de ligne de commande recherchent [!DNL flashaccesstools.properties] dans le répertoire dans lequel vous exécutez les outils. Cependant, vous pouvez utiliser l&#39;option `-c` lorsque vous exécutez un outil de ligne de commande pour spécifier un autre emplacement pour le [!DNL flashaccesstools.properties] par défaut. Vous pouvez également utiliser `-c` pour spécifier un autre fichier de configuration.

Les fichiers de configuration des outils de ligne de commande utilisent le format *fichier de propriétés Java*, pour lequel les règles suivantes s’appliquent :

* Echapper aux barres obliques inverses avec une barre oblique inverse supplémentaire.

   Par exemple, sur un ordinateur Windows, pour spécifier le fichier [!DNL C:\credentials.pfx], vous devez le saisir sous la forme [!DNL C:\\credentials.pfx] ou `C:/credentials.pfx`. Pour spécifier un fichier sur un serveur réseau Windows, vous devez entrer `\\\\server\\folder\\filename.pfx`
* N’incluez que des caractères *latins-1*.

   Pour utiliser des caractères non-*Latin-1*, vous devez utiliser la séquence d’échappement Unicode appropriée. Vous pouvez éventuellement appliquer l&#39;outil [!DNL native2ascii] (inclus avec Java) à vos entrées de fichier de configuration.
