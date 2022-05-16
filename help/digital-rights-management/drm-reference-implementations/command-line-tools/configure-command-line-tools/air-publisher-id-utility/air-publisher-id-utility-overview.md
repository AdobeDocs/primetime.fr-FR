---
title: Présentation
description: Présentation
copied-description: true
exl-id: 07f2ef0b-c6aa-4574-a3ae-18685a090cf2
source-git-commit: a1fc67b708f3d5821532d3827639adbadf15f6b4
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Utilitaire AIR Publisher ID {#air-publisher-id-utility}

Lorsque vous créez un fichier AIR, l’outil de développement AIR (ADT) génère automatiquement un identifiant d’éditeur. Utilitaire AIR Publisher ID ( [!DNL AdobePublisherIDUtility.jar]) calcule l’identifiant d’éditeur d’une application AIR.

L’identifiant de l’éditeur est unique au certificat que vous utilisez pour créer un fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, toutes les applications AIR ont le même identifiant d’éditeur. Une version d’AIR qui succède à la version 1.5.2 n’ajoute pas l’identifiant d’éditeur généré à un fichier. Par conséquent, si vous prévoyez d’utiliser une liste autorisée d’application AIR, utilisez cet outil pour déterminer l’identifiant de l’éditeur.

>[!NOTE]
>
>L’identifiant de l’éditeur utilisé pour l’application des listes autorisées AIR n’est pas identique à l’identifiant de l’éditeur spécifié par l’éditeur de l’application dans le [!DNL application.xml] fichier .

## Utilisation de la ligne de commande de l’utilitaire AIR Publisher ID {#air-publisher-id-utility-command-line-usage}

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

* `signaturefile` spécifie un chemin d’accès au de l’application AIR [!DNL signatures.xml] fichier situé dans les applications [!DNL META-INF] directory

* `signingcert` spécifie le certificat utilisé pour signer une application AIR

>[!NOTE]
>
>Pour déterminer l’ID d’éditeur d’une application Android, vous devez utiliser la variable `-s` pour spécifier le certificat utilisé pour signer le package de l’application Android (APK). Primetime DRM est requis pour créer des applications Android capables de lire du contenu protégé par DRM Primetime.
