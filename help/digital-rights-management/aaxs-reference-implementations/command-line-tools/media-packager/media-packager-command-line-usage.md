---
title: Utilisation de la ligne de commande
description: Utilisation de la ligne de commande
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Utilisation de la ligne de commande {#command-line-usage}

Avant d’utiliser Media Packager, assurez-vous de respecter les exigences répertoriées dans Exigences et que le fichier de configuration contient les informations requises (voir Fichier de configuration dans la section *Utilisation des implémentations de référence d’accès Adobe*.

Media Packager se trouve dans la variable [!DNL \Reference Implementation\Command Line tools] répertoire sur le DVD. Pour chiffrer un seul fichier, utilisez la syntaxe suivante :

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
* `dest` indique l’emplacement d’écriture du contenu chiffré. Si un répertoire est spécifié, le fichier chiffré sera enregistré dans ce dossier avec le même nom de fichier que le fichier source, mais le répertoire ne doit pas être celui qui contient le fichier source.

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

* `sourcefiles` est une série d’entrées source délimitées par des espaces qui représentent les fichiers à chiffrer.
* `dest-directory` indique l’emplacement d’écriture du contenu chiffré. Les fichiers cryptés seront enregistrés dans ce dossier avec les mêmes noms que les fichiers source, mais le répertoire ne doit pas être celui contenant les fichiers source.

Pour afficher des informations sur un fichier chiffré, utilisez la syntaxe suivante :

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` est le fichier chiffré.

Pour afficher des informations sur un fichier de métadonnées, utilisez la syntaxe suivante :

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` est un [!DNL .metadata] fichier contenant les métadonnées DRM.

>[!NOTE]
>
>Lors du conditionnement, Media Packager ne génère plus de fichier .header par défaut. Pour générer ce fichier, utilisez la méthode `-h` lors de l’emballage.

Le tableau suivant contient des descriptions des options de ligne de commande affichées dans la syntaxe ci-dessus :

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’emplacement du fichier de configuration. Si cette option n’est pas utilisée, Media Packager recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur un fichier qui a déjà été compressé. Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Affiche des informations sur les métadonnées existantes. Les fichiers source et de destination ne sont pas requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez cette option avec <span class="codeph"> -d </span> pour extraire des stratégies à partir d’un fichier compressé. Un fichier sera créé dans le même répertoire que le fichier chiffré à l’aide du nom de fichier et de l’identifiant de stratégie. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisation avec <span class="codeph"> -d </span> pour extraire l’en-tête DRM d’un fichier empaqueté. Un fichier est créé dans le même répertoire que le fichier chiffré, à l’aide du nom de fichier et de l’extension <span class="filepath"> .header </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique un identifiant unique pour ce élément de contenu. Si aucun identifiant n’est spécifié, le nom du fichier destfile est utilisé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> value </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie une clé/valeur personnalisée à ajouter aux métadonnées de contenu. Multiple <span class="codeph"> -k </span> Les options peuvent être spécifiées. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez cette option avec <span class="codeph"> -d </span> pour extraire les métadonnées d’un fichier empaqueté. Un fichier sera créé dans le même répertoire que le fichier chiffré à l’aide du nom de fichier et de l’extension. <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et <span class="codeph"> -o </span> n’est pas définie, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Remplace le fichier de destination sans invite, s’il existe déjà. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom du fichier contenant la stratégie. Si la stratégie nécessite l’enregistrement de domaine avec un serveur qui utilise un certificat de transport différent de celui spécifié dans le fichier de propriétés, le certificat de transport de domaine doit également être fourni. </p> <p class="- topic/p ">Multiple <span class="codeph"> -p </span> Les options peuvent être spécifiées et le client utilisera la première par défaut. Les valeurs spécifiées sur la ligne de commande sont prioritaires sur celles spécifiées dans le fichier de configuration. </p> </td> 
  </tr> 
 </tbody> 
</table>
