---
description: L’utilitaire SWF Hash Calculator calcule le résumé d’une application SWF qui se trouve dans un fichier.
title: Calculatrice de hachage SWF
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---


# Calculatrice de hachage SWF{#swf-hash-calculator}

L’utilitaire SWF Hash Calculator calcule le résumé d’une application SWF qui se trouve dans un fichier.

Pour exécuter le hasher, tapez :

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

Vous pouvez utiliser cette valeur pour spécifier le résumé SWF dans [!DNL flashaccess-tenant.xml].
