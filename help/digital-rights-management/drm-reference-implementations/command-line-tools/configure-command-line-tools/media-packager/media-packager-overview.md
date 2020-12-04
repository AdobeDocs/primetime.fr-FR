---
description: 'null'
seo-description: 'null'
seo-title: Présentation
title: Présentation
uuid: f4474837-9460-479d-89c2-dd697e0fb997
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---


# DRM Media Packager {#media-packager}

Utilisez Media Packager ( [!DNL AdobePackager.jar]) pour spécifier une stratégie DRM à appliquer à votre contenu et pour spécifier la partie du contenu à chiffrer. Par exemple, vous pouvez spécifier que l’outil de création de package doit chiffrer les données vidéo, mais pas les données audio.

Avant d’exécuter [!DNL AdobePackager.jar], vous devez définir les propriétés dans la section Propriétés de Media Packager de votre fichier de configuration.

>[!NOTE]
>
>Vous pouvez également spécifier toutes les propriétés Media Packager à partir de la ligne de commande.

## Utilisation de la ligne de commande de Media Packager {#media-packager-command-line-usage}

**Package un fichier :**

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

* `source` - nom du fichier à chiffrer.
* `dest` - Nom du fichier chiffré obtenu.

   Si vous spécifiez un répertoire, le fichier chiffré est automatiquement enregistré dans le répertoire spécifié avec le même nom de fichier que celui que vous avez spécifié comme fichier source. Cependant, vous ne pouvez pas spécifier un répertoire de destination incluant le fichier source.

**compresser plusieurs fichiers avec la même clé**  (pour la prise en charge de débits multiples) :

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

* `sourcefiles` - Série d&#39;entrées source délimitées par des espaces blancs pour les fichiers à chiffrer.
* `dest-directory` - Répertoire de destination dans lequel vous souhaitez écrire du contenu chiffré. Les fichiers chiffrés sont automatiquement enregistrés dans ce répertoire en utilisant les mêmes noms de fichier que les fichiers source. Cependant, le répertoire de destination ne peut pas inclure de fichiers source.

**Informations sur la vue d’un fichier chiffré :**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**Informations sur la vue d’un fichier de métadonnées :**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` est un  [!DNL .metadata] fichier contenant des métadonnées DRM.

>[!NOTE]
>
>Lors de la création d’un pack, Media Packager ne peut plus générer de fichier [!DNL .header] par défaut. Pour générer un fichier [!DNL .header], utilisez l&#39;option `-h` lors de l&#39;assemblage.

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez ni nom ni emplacement, DRM Media Packager recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail actuel. </p> <p>Remarque :  Les options que vous spécifiez sur la ligne de commande sont prioritaires sur les options que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Permet d’accéder aux informations de vue sur un fichier qui a déjà été compressé. </p> <p class="- topic/p ">Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> fichier de métadonnées </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Permet d’accéder aux informations de vue sur les métadonnées existantes. </p> <p class="- topic/p ">Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrait les stratégies DRM d'un fichier compressé lorsque vous appliquez cette option conjointement avec l'option <span class="codeph"> -d </span>. </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le répertoire dans lequel se trouve le fichier chiffré avec un nom de fichier et un identifiant de stratégie DRM. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrait l’en-tête DRM d’un fichier compressé lorsque vous appliquez cette option conjointement avec l’option <span class="codeph"> -d </span>. </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le répertoire dans lequel se trouve le fichier chiffré, avec le nom du fichier et l'extension <span class="filepath"> .header </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique un identifiant unique pour ce segment de contenu. </p> <p class="- topic/p ">Si vous ne spécifiez aucun identifiant, le nom du fichier destfile est automatiquement appliqué. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> clé </span>= <span class="+ topic/ph pr-d/codeph codeph"> valeur </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé/valeur personnalisée à ajouter aux métadonnées de contenu. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs options <span class="codeph"> -k </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Extrayez les métadonnées d’un fichier compressé lorsque vous appliquez cette option conjointement avec l’option <span class="codeph"> -d </span>. </p> <p class="- topic/p ">Un fichier est automatiquement créé dans le même répertoire que le fichier chiffré avec un nom de fichier et une extension <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. </p> <p class="- topic/p ">Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Remplace le fichier de destination sans que vous ne soyez invité à le faire, sauf s’il existe déjà. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> nom de fichier [domaine-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie le nom du fichier qui inclut la stratégie DRM. </p> <p class="- topic/p ">Si la stratégie DRM requiert l'enregistrement de domaine auprès d'un serveur qui utilise un certificat de transport autre que celui que vous avez spécifié dans le fichier de propriétés, vous devez fournir le certificat de transport de domaine. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs options <span class="codeph"> -p </span>. Le client applique toujours la première option par défaut. Les valeurs que vous avez spécifiées sur la ligne de commande sont prioritaires sur celles que vous avez spécifiées dans le fichier de configuration. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés de configuration {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>Pour les noms de propriété qui incluent* n*, *n* représente un entier qui début avec 1 et augmente pour chaque instance de la propriété.

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
   <td colname="2" class="- topic/entry "> Indique si le contenu vidéo doit être chiffré. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Indique s’il faut chiffrer l’audio. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Indique si les données de script doivent être chiffrées dans mp4s. </p> <p><i class="+ topic/ph hi-d/i ">Les balises de données </i> onMetaData et  <i class="+ topic/ph hi-d/i "></i> onXMPscript ne sont jamais chiffrées, même si vous activez cette option. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le niveau de chiffrement vidéo. </p> <p class="- topic/p ">Une valeur <span class="codeph"> high</span> est utilisée pour chiffrer tout le contenu vidéo, tandis que des valeurs <span class="codeph"> medium</span> et <span class="codeph"> low</span> sont utilisées pour chiffrer des portions du contenu vidéo pour les fichiers mp4 qui incluent du contenu H.264. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si la valeur est supérieure à 0, le nombre spécifié de secondes de contenu au début du fichier n’est pas chiffré. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier de certificat du serveur de licences utilisé pour chiffrer la clé. </p> <p class="- topic/p ">La propriété <span class="codeph"> encrypt.keys.asymmetric.certfile</span> spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Cette propriété est utilisée à plusieurs reprises pour créer une liste de stratégies DRM à appliquer au contenu. <span class="codeph"> </span> représente un entier dont la valeur est supérieure ou égale à 1. Le client utilise par défaut la première instance. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du serveur de licences </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Certificat de transport pour le serveur de licences. </p> <p class="- topic/p ">Cette propriété spécifie un fichier <span class="filepath"> .cer</span> qui inclut uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le fichier PKCS12 qui contient les informations d’identification de packager pour la signature de contenu. </p> <p class="- topic/p ">Le <span class="codeph"> encrypt.sign.certfile</span> doit faire référence à un fichier <span class="filepath"> .pfx</span> qui inclut un certificat et une clé privée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">mot de passe que vous pouvez appliquer pour protéger le fichier spécifié par <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Définit la version minimale du serveur requise pour émettre des licences pour le contenu en cours de création de package. </p> <p class="- topic/p ">Spécifiez x (pour Primetime DRM x.0) où x représente un numéro de version majeur. Les versions de serveurs antérieures à Adobe Primetime version 3.0 ne prennent pas en charge ce paramètre. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si une stratégie DRM <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> nécessite l'enregistrement du domaine avec un serveur qui prend en charge un certificat de transport autre que celui que vous avez spécifié dans <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>, vous devez fournir le certificat de transport de domaine dont vous avez besoin. </p> <p class="- topic/p ">Cette propriété spécifie un fichier qui inclut uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé de licence. </p> <p class="- topic/p ">Si vous ne spécifiez pas de clé, celle-ci est générée de manière aléatoire. Si vous n’activez pas la rotation des clés, vous pouvez utiliser cette clé pour chiffrer le contenu. </p> <p class="- topic/p ">Lorsque vous activez la rotation des clés, vous pouvez utiliser cette clé pour protéger les clés de rotation. La clé doit avoir une longueur de 16 octets et être spécifiée en tant que valeurs hexadécimales. L’espace entre les valeurs hexadécimales est facultatif. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique si la rotation des clés est activée. </p> <p class="- topic/p ">Si la valeur est définie sur false (paramètre par défaut), la rotation des clés est désactivée et le CEK maître est utilisé pour chiffrer tous les échantillons du contenu. </p> <p class="- topic/p ">Si elle est définie sur true, la rotation des clés est activée et différentes clés peuvent être utilisées pour chiffrer des segments de tout contenu. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Séquence de clés pivotées que vous pouvez spécifier pour chiffrer le contenu lorsque la rotation des clés est activée. </p> <p class="- topic/p ">Si vous ne spécifiez aucune clé, les clés sont générées de manière aléatoire. Les clés doivent avoir une longueur de 16 octets et être spécifiées en tant que valeurs hexadécimales. </p> <p class="- topic/p ">L’espace entre les valeurs hexadécimales est facultatif. <i class="+ topic/ph hi-d/i "></i> ne doit pas augmenter monotoniquement, en commençant par 1. Lorsque vous spécifiez plusieurs clés, les clés sont alors parcourues dans l’ordre indiqué. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’intervalle en secondes pendant lequel vous pouvez appliquer une clé de rotation pour chiffrer des échantillons de contenu. </p> <p class="- topic/p ">Une fois l’intervalle de temps écoulé au cours duquel le contenu a été chiffré, la clé de rotation suivante est alors appliquée. Si vous avez activé la rotation des clés, mais que vous n’avez spécifié aucun intervalle de temps, les clés sont automatiquement pivotées toutes les 15 minutes. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si cette option est définie sur true, un serveur de licences à partir duquel des licences peuvent être obtenues n’est pas disponible. </p> <p class="- topic/p ">Les licences doivent être incorporées ou obtenues hors bande. La valeur par défaut est définie sur false, sauf si vous spécifiez une autre valeur. Cette option est uniquement prise en charge dans Primetime DRM Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>