---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# DRM Media Packager {#media-packager}

Utilisation de Media Packager ( [!DNL AdobePackager.jar]) pour spécifier une stratégie DRM à appliquer à votre contenu et spécifier la partie du contenu à chiffrer. Par exemple, vous pouvez spécifier que le programme de package chiffre les données vidéo, mais pas les données audio.

Avant l’exécution [!DNL AdobePackager.jar], vous devez définir les propriétés dans la section Propriétés de Media Packager de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés Media Packager à partir de la ligne de commande.

## Utilisation de la ligne de commande de Media Packager {#media-packager-command-line-usage}

**Module un fichier :**

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source` : nom du fichier que vous souhaitez chiffrer.
* `dest` - Nom du fichier chiffré obtenu.

  Si vous spécifiez un répertoire, le fichier chiffré est automatiquement enregistré dans le répertoire spécifié avec le même nom de fichier que celui que vous avez spécifié comme fichier source. Cependant, vous ne pouvez pas spécifier de répertoire de destination qui inclut le fichier source.

**Regroupez plusieurs fichiers avec la même clé** (pour la prise en charge de débits multiples) :

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles` - Série d’entrées source délimitées par des espaces pour les fichiers que vous souhaitez chiffrer.
* `dest-directory` - Répertoire de destination dans lequel vous souhaitez écrire du contenu chiffré. Les fichiers cryptés sont automatiquement enregistrés dans ce répertoire en utilisant les mêmes noms que les fichiers source. Cependant, le répertoire de destination ne peut pas inclure de fichiers source.

**Affichez les informations sur un fichier chiffré :**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**Affichage des informations sur un fichier de métadonnées :**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` est un [!DNL .metadata] qui comprend des métadonnées DRM.

>[!NOTE]
>
>Lors du conditionnement, Media Packager ne peut plus générer d’événement [!DNL .header] par défaut. Pour générer un [!DNL .header] , utilisez le fichier `-h` lors de l’emballage.

**Tableau 3 : Options**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez aucun nom ou emplacement, DRM Media Packager recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail actuel. </p> <p>Remarque : les options que vous spécifiez sur la ligne de commande sont prioritaires sur celles que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Permet d’afficher des informations sur un fichier qui a déjà été compressé. </p> <p class="- topic/p ">Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Permet d’afficher des informations sur les métadonnées existantes. </p> <p class="- topic/p ">Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrait les stratégies DRM d’un fichier empaqueté lorsque vous appliquez cette option conjointement avec la fonction <span class="codeph"> -d </span> . </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le répertoire où se trouve le fichier chiffré avec un nom de fichier et un identifiant de stratégie DRM. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrait l’en-tête DRM d’un fichier empaqueté lorsque vous appliquez cette option conjointement avec la fonction <span class="codeph"> -d </span> . </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le répertoire où se trouve le fichier crypté, avec le nom du fichier et l'extension. <span class="filepath"> .header </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique un identifiant unique pour ce segment de contenu. </p> <p class="- topic/p ">Si vous ne spécifiez aucun identifiant, le nom du fichier destfile est automatiquement appliqué. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé/valeur personnalisée à ajouter aux métadonnées de contenu. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -k </span> options. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extraire les métadonnées d’un fichier empaqueté lorsque vous appliquez cette option conjointement avec la fonction <span class="codeph"> -d </span> . </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le même répertoire que le fichier chiffré avec un nom de fichier et un <span class="codeph"> .metadata </span> extension . </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. </p> <p class="- topic/p ">Si le fichier de destination existe déjà et <span class="codeph"> -o </span> n’est pas définie, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Remplace le fichier de destination sans que vous ne soyez invité à le faire, sauf s’il existe déjà. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom du fichier qui comprend la stratégie DRM. </p> <p class="- topic/p ">Si la stratégie DRM nécessite l’enregistrement de domaine avec un serveur qui utilise un certificat de transport autre que celui que vous avez spécifié dans le fichier de propriétés, vous devez fournir le certificat de transport de domaine. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -p </span> options. Le client applique toujours la première option par défaut. Les valeurs que vous avez spécifiées sur la ligne de commande sont prioritaires sur celles que vous avez spécifiées dans le fichier de configuration. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>Pour les noms de propriétés qui incluent* n*, *n* représente un entier qui commence par 1 et augmente pour chaque instance de la propriété.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Propriété </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> Indique s’il faut chiffrer le contenu vidéo. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Indique s’il faut chiffrer l’audio. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Indique s’il faut chiffrer les données de script dans mp4s. </p> <p><i class="+ topic/ph hi-d/i ">onMetaData</i> et <i class="+ topic/ph hi-d/i ">onXMP</i> les balises de données de script ne sont jamais chiffrées, même si vous activez cette option. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le niveau de chiffrement vidéo. </p> <p class="- topic/p ">Une valeur de <span class="codeph"> high</span> est utilisé pour chiffrer tout le contenu vidéo, tandis que les valeurs de <span class="codeph"> medium</span> et <span class="codeph"> low</span> sont utilisés pour chiffrer des parties du contenu vidéo pour les fichiers mp4 contenant du contenu H.264. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si la valeur est supérieure à 0, le nombre de secondes de contenu spécifié au début du fichier n’est pas chiffré. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le fichier de certificat du serveur de licences utilisé pour chiffrer la clé. </p> <p class="- topic/p ">La variable <span class="codeph"> encrypt.keys.asymmetric.certfile</span> spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Cette propriété est utilisée à plusieurs reprises pour créer une liste de stratégies DRM à appliquer au contenu. <span class="codeph"> n</span> représente un entier dont la valeur est supérieure ou égale à 1. Le client utilise par défaut la première instance. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du serveur de licences </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le certificat de transport du serveur de licences. </p> <p class="- topic/p ">Cette propriété spécifie une propriété <span class="filepath"> .cer</span> qui inclut uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le fichier PKCS12 qui comprend les informations d’identification du module pour la signature du contenu. </p> <p class="- topic/p ">La variable <span class="codeph"> encrypt.sign.certfile</span> doit faire référence à une <span class="filepath"> .pfx</span> qui comprend un certificat et une clé privée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Mot de passe que vous pouvez appliquer pour protéger le fichier qui a été spécifié par <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Définit la version minimale du serveur requise pour émettre des licences pour le contenu en cours de package. </p> <p class="- topic/p ">Spécifiez x (pour Primetime DRM x.0) où x représente un numéro de version majeur. Les versions de serveurs antérieures à Adobe Primetime version 3.0 ne prennent pas en charge ce paramètre. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si une stratégie DRM <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> nécessite l’enregistrement du domaine avec un serveur prenant en charge un certificat de transport autre que celui spécifié dans <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>, vous devez ensuite fournir le certificat de transport de domaine nécessaire. </p> <p class="- topic/p ">Cette propriété spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé de licence. </p> <p class="- topic/p ">Si vous ne spécifiez aucune clé, celle-ci est générée de manière aléatoire. Lorsque vous n’activez pas la rotation des clés, vous pouvez utiliser cette clé pour chiffrer le contenu. </p> <p class="- topic/p ">Lorsque vous activez la rotation des clés, vous pouvez utiliser cette clé pour protéger les clés de rotation. La clé doit avoir une longueur de 16 octets et être spécifiée sous la forme de valeurs hexadécimales. Un espace blanc entre les valeurs hexadécimales est facultatif. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique si la rotation des clés est activée. </p> <p class="- topic/p ">S’il est défini sur false, qui est le paramètre par défaut, la rotation de clé est désactivée et le CEK maître est utilisé pour chiffrer tous les exemples dans le contenu. </p> <p class="- topic/p ">Si la valeur est définie sur true, la rotation des clés est activée et différentes clés peuvent être utilisées pour chiffrer les segments de n’importe quel contenu. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Séquence de clés pivotées que vous pouvez spécifier pour chiffrer le contenu lorsque la rotation de clés est activée. </p> <p class="- topic/p ">Si vous ne spécifiez aucune clé, les clés sont générées de manière aléatoire. Les clés doivent avoir une longueur de 16 octets et être spécifiées en tant que valeurs hexadécimales. </p> <p class="- topic/p ">Un espace blanc entre les valeurs hexadécimales est facultatif. <i class="+ topic/ph hi-d/i ">n</i> doit augmenter de manière monotone, en commençant par 1. Lorsque vous spécifiez plusieurs clés, les clés sont parcourues à l’aide de l’ordre indiqué. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’intervalle en secondes au cours duquel vous pouvez appliquer une clé de rotation pour chiffrer des exemples de contenu. </p> <p class="- topic/p ">Une fois l’intervalle de temps écoulé au cours duquel le contenu a été chiffré, la clé de rotation suivante est alors appliquée. Si vous avez activé la rotation des clés mais n’avez spécifié aucun intervalle de temps, les clés sont automatiquement pivotées toutes les 15 minutes. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si cette option est définie sur true, un serveur de licences à partir duquel des licences peuvent être obtenues n’est pas disponible. </p> <p class="- topic/p ">Les licences doivent être incorporées ou obtenues hors bande. La valeur par défaut est définie sur false, sauf si vous spécifiez une autre valeur. Cette option est uniquement prise en charge dans Primetime DRM Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>
