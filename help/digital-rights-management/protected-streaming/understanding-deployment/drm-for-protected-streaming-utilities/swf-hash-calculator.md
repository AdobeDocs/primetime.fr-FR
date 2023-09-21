---
description: L’utilitaire SWF Hash Calculator calcule le résumé d’une application de SWF qui se trouve dans un fichier.
title: calculateur de hachage SWF
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# calculateur de hachage SWF{#swf-hash-calculator}

L’utilitaire SWF Hash Calculator calcule le résumé d’une application de SWF qui se trouve dans un fichier.

Pour exécuter le hashher, saisissez :

```
Hasher.bat 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

ou

```
java -jar libs/flashaccess-hasher.jar 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

L’utilitaire affiche le message suivant :

```
SWF Hash: 
<i class="+ topic ph hi-d="" i "="">
  hash-of-swf
</i class="+ topic>
```

Vous pouvez utiliser cette valeur pour spécifier le condensé du SWF dans [!DNL flashaccess-tenant.xml].
