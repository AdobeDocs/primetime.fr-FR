---
title: Calculatrice de hachage SWF
description: Calculatrice de hachage SWF
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Calculateur de hachage SWF{#swf-hash-calculator}

L’utilitaire SWF Hash Calculator calculait le résumé d’une application SWF située dans un fichier. Pour exécuter le hasher, exécutez la commande :

```
Hasher.bat filename.swf
```

ou la commande :

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

L&#39;utilitaire génère le message suivant :

```
SWF Hash: hash-of-swf
```

Cette valeur peut être utilisée pour spécifier le résumé SWF dans [!DNL flashaccess-tenant.xml].
