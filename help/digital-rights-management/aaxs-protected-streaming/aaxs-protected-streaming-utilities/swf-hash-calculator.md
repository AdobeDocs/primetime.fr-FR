---
seo-title: Calculatrice de hachage SWF
title: Calculatrice de hachage SWF
uuid: c1823208-92d9-47c5-b550-f9cc370b543d
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
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
