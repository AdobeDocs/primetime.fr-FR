---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
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

* 
   * `signaturefile`* indique le chemin d’accès au fichier signatures.xml de l’application AIR, situé dans le  [!DNL META-INF] répertoire des applications.

* `signingcert` spécifie le certificat utilisé pour signer l&#39;application AIR

>[!NOTE]
>
>Pour déterminer l’ID d’éditeur d’une application iOS, utilisez l’option `-s` et spécifiez le certificat utilisé pour signer l’application iOS. ***Adobe Primetime est nécessaire pour créer des applications iOS capables de lire du contenu*** protégé par Access.

