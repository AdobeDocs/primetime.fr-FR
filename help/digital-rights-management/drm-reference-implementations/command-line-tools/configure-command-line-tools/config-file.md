---
description: 'null'
seo-description: 'null'
seo-title: A propos des fichiers de configuration des outils de ligne de commande
title: A propos des fichiers de configuration des outils de ligne de commande
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155

---


# A propos des fichiers de configuration des outils de ligne de commande{#about-command-line-tools-configuration-files}

Les outils de ligne de commande recherchent [!DNL flashaccesstools.properties] dans le répertoire dans lequel vous exécutez les outils. Cependant, vous pouvez utiliser cette `-c` option lorsque vous exécutez un outil de ligne de commande pour spécifier un autre emplacement pour la valeur par défaut [!DNL flashaccesstools.properties]. Vous pouvez également spécifier `-c` un fichier de configuration différent.

Les fichiers de configuration des outils de ligne de commande utilisent le format de fichier *de propriétés* Java, pour lequel les règles suivantes s’appliquent :

* Echapper aux barres obliques inverses avec une barre oblique inverse supplémentaire.

   Par exemple, sur un ordinateur Windows, pour spécifier le [!DNL C:\credentials.pfx] fichier, vous devez le saisir sous [!DNL C:\\credentials.pfx] ou `C:/credentials.pfx`. Pour spécifier un fichier sur un serveur réseau Windows, vous devez saisir `\\\\server\\folder\\filename.pfx`
* N’incluez que des caractères *latins-1* .

   Pour utiliser des caractères non *latins-1* , vous devez utiliser la séquence d’échappement Unicode appropriée. Vous pouvez éventuellement appliquer l’ [!DNL native2ascii] outil (inclus avec Java) à vos entrées de fichier de configuration.
