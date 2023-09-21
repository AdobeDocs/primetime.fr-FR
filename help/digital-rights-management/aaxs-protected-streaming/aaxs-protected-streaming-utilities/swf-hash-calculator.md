---
title: Calculateur de hachage du SWF
description: Calculateur de hachage du SWF
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# Calculateur de hachage du SWF{#swf-hash-calculator}

L’utilitaire SWF Hash Calculator calculait le résumé d’une application de SWF située dans un fichier. Pour exécuter la barre d’outils, exécutez la commande :

```
Hasher.bat filename.swf
```

ou la commande :

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

L’utilitaire génère le message suivant :

```
SWF Hash: hash-of-swf
```

Cette valeur peut être utilisée pour spécifier le condensé du SWF dans [!DNL flashaccess-tenant.xml].
