---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

* `signaturefile` spécifie le chemin d’accès au fichier signatures.xml de l’application AIR, situé dans les applications. [!DNL META-INF] directory

* `signingcert` spécifie le certificat utilisé pour signer l’application AIR

>[!NOTE]
>
>Pour déterminer l’identifiant d’éditeur d’une application iOS, utilisez la variable `-s` et indiquez le certificat utilisé pour signer l’application iOS. ***Adobe Primetime est requis pour créer des applications iOS capables de lire du contenu protégé par accès***.
