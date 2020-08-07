---
seo-title: Présentation
title: Présentation
uuid: f45c6b58-53c5-41e0-be3d-590231dd214a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Utilitaire d’ID d’éditeur AIR {#air-publisher-id-utility}

Lorsque vous créez un fichier AIR, l’outil ADT (AIR Developer Tool) génère automatiquement un identifiant d’éditeur. L’utilitaire d’identification de l’éditeur AIR ( [!DNL AdobePublisherIDUtility.jar]) calcule l’identifiant de l’éditeur pour une application AIR.

L’ID d’éditeur est unique au certificat que vous utilisez pour créer un fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, toutes les applications AIR ont le même ID d’éditeur. Une version AIR qui succède à la version 1.5.2 n’ajoute pas l’identifiant d’éditeur généré à un fichier. Par conséquent, si vous prévoyez d’utiliser une liste autorisée d’applications AIR, utilisez cet outil pour déterminer l’identifiant de l’éditeur.

>[!NOTE]
>
>L’ID d’éditeur utilisé pour l’application de la liste autorisée AIR n’est pas identique à l’ID d’éditeur spécifié par l’éditeur de l’application dans le [!DNL application.xml] fichier de l’application.

## Utilisation de la ligne de commande de l’utilitaire d’identification de l’éditeur AIR {#air-publisher-id-utility-command-line-usage}

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
   * `signaturefile`* indique un chemin d’accès au [!DNL signatures.xml] fichier de l’application AIR, situé dans le [!DNL META-INF] répertoire des applications.

* `signingcert` spécifie le certificat utilisé pour signer une application AIR

>[!NOTE]
>
>Pour déterminer l&#39;ID d&#39;éditeur d&#39;une application Android, vous devez utiliser l&#39; `-s` option pour spécifier le certificat utilisé pour signer le package d&#39;application Android (APK). Primetime DRM est nécessaire pour créer des applications Android capables de lire du contenu protégé par DRM Primetime.