---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: 5f24f18d-09ef-400a-9404-50a9fcf4316d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# Utilisation de la ligne de commande {#command-line-usage}

Avant d’utiliser Media Packager, assurez-vous de respecter les exigences répertoriées dans la section Conditions requises et assurez-vous que le fichier de configuration contient les informations requises (voir Fichier de configuration dans la section *Utilisation des implémentations* de référence d’accès à l’Adobe).

Media Packager se trouve dans le [!DNL \Reference Implementation\Command Line tools] répertoire du DVD. Pour chiffrer un fichier unique, utilisez la syntaxe suivante :

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

* `source` est le fichier à chiffrer.
* `dest` indique où le contenu chiffré sera écrit. Si un répertoire est spécifié, le fichier chiffré est enregistré dans ce dossier en utilisant le même nom de fichier que le fichier source, mais le répertoire ne doit pas être celui qui contient le fichier source.

Pour chiffrer plusieurs fichiers avec la même clé (pour la prise en charge de débits multiples), utilisez la syntaxe suivante :

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

* `sourcefiles` est une série d’entrées source délimitées par des espaces blancs représentant les fichiers à chiffrer.
* `dest-directory` indique où le contenu chiffré sera écrit. Les fichiers chiffrés seront enregistrés dans ce dossier en utilisant les mêmes noms de fichier que les fichiers source, mais le répertoire ne doit pas être celui qui contient les fichiers source.

Pour vue des informations sur un fichier chiffré, utilisez la syntaxe suivante :

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` est le fichier chiffré.

Pour vue des informations sur un fichier de métadonnées, utilisez la syntaxe suivante :

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` est un [!DNL .metadata] fichier contenant les métadonnées DRM.

>[!NOTE]
>
>Lors de l’assemblage, Media Packager ne génère plus par défaut un fichier .header. Pour générer ce fichier, utilisez l’ `-h` option lors de l’assemblage.

Le tableau suivant contient la description des options de ligne de commande affichées dans la syntaxe ci-dessus :

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, Media Packager recherchera <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur un fichier déjà compressé. Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm, fichier <span class="+ topic/ph pr-d/codeph codeph"> de métadonnées </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur les métadonnées existantes. Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez cette option avec <span class="codeph"> -d </span> pour extraire les stratégies d’un fichier compressé. Un fichier est créé dans le même répertoire que le fichier chiffré à l’aide du nom de fichier et de l’identifiant de stratégie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez avec <span class="codeph"> -d </span> pour extraire l’en-tête DRM d’un fichier compressé. Un fichier est créé dans le même répertoire que le fichier chiffré, en utilisant le nom de fichier et l’extension <span class="filepath"> .header. </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique un identifiant unique pour cet élément de contenu. Si aucun identifiant n’est spécifié, le nom du fichier destfile est utilisé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= valeur <span class="+ topic/ph pr-d/codeph codeph"> </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé/valeur personnalisée à ajouter aux métadonnées de contenu. Plusieurs options <span class="codeph"> -k </span> peuvent être spécifiées. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez cette option avec <span class="codeph"> -d </span> pour extraire les métadonnées d’un fichier compressé. Un fichier sera créé dans le même répertoire que le fichier chiffré en utilisant le nom de fichier et l'extension <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Remplace le fichier de destination sans invite, s’il existe déjà. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p nom <span class="+ topic/ph pr-d/codeph codeph"> de fichier [domaine-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom du fichier contenant la stratégie. Si la stratégie requiert l’enregistrement de domaine auprès d’un serveur qui utilise un certificat de transport différent de celui spécifié dans le fichier de propriétés, le certificat de transport de domaine doit également être fourni. </p> <p class="- topic/p ">Plusieurs <span class="codeph"> options </span> -p peuvent être spécifiées et le client utilisera la première par défaut. Les valeurs spécifiées sur la ligne de commande sont prioritaires sur celles spécifiées dans le fichier de configuration. </p> </td> 
  </tr> 
 </tbody> 
</table>

