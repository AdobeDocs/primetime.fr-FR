---
title: A propos des fichiers de configuration des outils de ligne de commande
description: A propos des fichiers de configuration des outils de ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# A propos des fichiers de configuration des outils de ligne de commande{#about-command-line-tools-configuration-files}

Les outils de ligne de commande recherchent [!DNL flashaccesstools.properties] dans le répertoire dans lequel vous exécutez les outils. Cependant, vous pouvez utiliser la variable `-c` lorsque vous exécutez un outil de ligne de commande pour spécifier un autre emplacement pour la valeur par défaut. [!DNL flashaccesstools.properties]. Vous pouvez également utiliser `-c` pour spécifier un autre fichier de configuration.

Les fichiers de configuration des outils de ligne de commande utilisent la variable *Fichier de propriétés Java* format pour lequel les règles suivantes s’appliquent :

* Échapper les barres obliques inverses avec une barre oblique inverse supplémentaire.

  Par exemple, sur un ordinateur Windows, pour spécifier la variable [!DNL C:\credentials.pfx] , vous devez le saisir comme [!DNL C:\\credentials.pfx] ou `C:/credentials.pfx`. Pour spécifier un fichier sur un serveur réseau Windows, vous devez saisir `\\\\server\\folder\\filename.pfx`
* Inclure uniquement *Latin-1* caractères.

  Pour utiliser non *Latin-1* , vous devez utiliser la séquence d’échappement Unicode appropriée. Vous pouvez éventuellement appliquer la variable [!DNL native2ascii] de votre outil (inclus avec Java) à vos entrées de fichier de configuration.
