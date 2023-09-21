---
description: Au-delà des paramètres de requête de base, les paramètres de requête facultatifs permettent au serveur manifest de fonctionner avec différents clients et situations.
title: Paramètres de requête facultatifs par client et par situation
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# Paramètres de requête facultatifs par client et par situation {#optional-query-parameters-by-client-and-situation}

Au-delà des paramètres de requête de base, les paramètres de requête facultatifs permettent au serveur manifest de fonctionner avec différents clients et situations.

## Insertion d’annonces avec Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}

Sur le réseau de diffusion de contenu Akamai, le serveur Akamai Edge fonctionne comme intermédiaire entre le client et le serveur de manifeste. Si vous utilisez également Ad Scaler, la variable `ptassetid` et `live` les paramètres de requête fournissent les informations requises à Akamai Edge.

La variable `ptassetid` est l’identifiant de l’éditeur pour sa ressource. Akamai l’utilise, plutôt que l’URL codée en base64 que vous fournissez dans le cadre de l’URL de demande, pour identifier la liste de lecture à fournir au serveur manifeste pour l’insertion de publicités.

La variable `live` fait la distinction entre le contenu en direct et la vidéo à la demande (VOD). Le serveur de manifeste a besoin de ces informations pour prendre en charge son interface rationalisée avec Akamai.

Voici un exemple d’URL présentant les paramètres relatifs à Akamai :

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## Insertion de publicités depuis TVSDK sur Xbox {#section_5DB405F4647240A0B83E72DE35D5EC80}

Un lecteur basé sur Primetime TVSDK sur Xbox n’a pas besoin de fournir des paramètres de requête supplémentaires au-delà des paramètres de base.

## Insertion d’annonces depuis TVSDK sur iOS avec Safari {#section_250E493A125E4F82940D19C7DA2AAB2E}

Un lecteur basé sur Primetime TVSDK sur iOS utilisant le navigateur Safari doit spécifier la variable `ptplayer` et `live` en plus des paramètres de requête de base.

Le serveur de manifeste reconnaît la variable `ptplayer` value `ios-mobileweb` et élimine le preroll du manifeste ad-stitched renvoyé.

La variable `live` indique au serveur manifest s’il doit renvoyer du contenu actif ou VOD.

Voici un exemple d’URL présentant les paramètres relatifs à iOS avec Safari :

```URL
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## Insertion d’une publicité à l’aide d’un format de repère de publicité personnalisé {#section_82AF880AAABE4BD4B593D906434D4D89}

Adobe fournit des noms pour les formats de repère de publicité qu’il ne prend pas en charge directement dans le package Primetime. Pour utiliser un tel format, indiquez son nom fourni par l’Adobe comme valeur de la variable `ptcueformat` .

Voici un exemple d’URL spécifiant un format de repère de publicité personnalisé :

```URL
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## Insertion d’annonces à l’aide d’indices publicitaires pour créer une chronologie FreeWheel pour VOD {#section_E0D830F5EEE24639819B975B90F6999F}

Pour que le contenu VOD contenant des indices publicitaires soit analysé et inclus dans une requête de publicité FreeWheel, définissez la valeur de la variable `ptcueformat` du paramètre `DPIsimple`.

Voici un exemple d’URL qui spécifie l’utilisation d’une chronologie FreeWheel pour VOD :

```URL
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## Insertion d’annonces à l’aide d’une chronologie personnalisée pour VOD {#section_F398F7659164463FA886A4CC787C7B5A}

Pour demander au serveur de manifeste d’insérer des publicités dans le contenu VOD selon une chronologie que vous fournissez, définissez la valeur de `pttimeline` à une chaîne spécifiant la chronologie. Voir [Format de la chronologie VOD](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md).

Voici un exemple d’URL qui utilise une chronologie personnalisée pour VOD :

```URL
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

Elle spécifie une coupure initiale d’une minute contenant jusqu’à deux publicités, suivie d’un segment de contenu de deux minutes, suivie d’une coupure de 30 secondes contenant jusqu’à deux publicités, suivie d’un segment de contenu de cinq minutes.

Le groupement publicitaire pour une chronologie de contenu personnalisée pour le contenu VOD se comporte comme suit :

* La publicité s’affiche à la limite de coupure la plus proche après l’heure de placement de la publicité spécifiée par le serveur de publicités.

* Les segments durent au moins deux secondes.

## Autorisation des segments TS {#section_BF855A4399DC42CB8C0586113A416BBC}

Adobe ne prend en charge cette fonctionnalité que pour le réseau de diffusion de contenu Akamai. La diffusion en continu en direct HTTP (HLS) fournit des segments de flux de transport (TS) à l’aide d’une liste de lecture M3U8 au niveau du flux. Plusieurs listes de lecture au niveau du flux sont fournies au client dans une liste de lecture de variante M3U8. Le client sélectionne un flux de liste de lecture à partir de la liste des variantes, puis télécharge les segments TS dans cette liste de lecture au niveau du flux un par un. En fonctionnement normal, le contenu demandé peut nécessiter une autorisation de cookie, que le serveur de manifeste traite de manière invisible en arrière-plan. Il extrait le cookie du contenu brut et ajoute un jeton approprié à l’URL à utiliser pour demander le flux de liste de lecture sélectionné.

Lorsque les paramètres de requête de l’URL du Bootstrap incluent `pttoken=true`, l’éditeur nécessite qu’un cookie soit utilisé pour demander chaque segment TS, plutôt qu’une seule fois pour l’ensemble du flux. Le serveur de manifeste associe ce cookie en tant que paramètre de requête à chaque URL de segment TS dans la liste de lecture de flux qu’il renvoie.
