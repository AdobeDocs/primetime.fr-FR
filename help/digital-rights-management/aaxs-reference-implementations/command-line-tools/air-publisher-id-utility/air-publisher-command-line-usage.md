---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Utilisation de la ligne de commande {#command-line-usage}

Pour exécuter l’outil, utilisez la syntaxe suivante :

```
java -jar AdobePublisherIDUtility.jar 
<i class="+ topic ph hi-d="" i "="">
 <i class="+ topic ph hi-d="" i "="">
  signaturefile 
  java -jar AdobePublisherIDUtility.jar -s 
  <i class="+ topic ph hi-d="" i "="">
    signingcert
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `signaturefile` indique le chemin d’accès au fichier signatures.xml de l’application AIR, situé dans le  [!DNL META-INF] répertoire des applications.

* `signingcert` spécifie le certificat utilisé pour signer l&#39;application AIR

>[!NOTE]
>
>Pour déterminer l’ID d’éditeur d’une application iOS, utilisez l’option `-s` et spécifiez le certificat utilisé pour signer l’application iOS. ***Adobe Primetime est nécessaire pour créer des applications iOS capables de lire du contenu*** protégé par Access.

