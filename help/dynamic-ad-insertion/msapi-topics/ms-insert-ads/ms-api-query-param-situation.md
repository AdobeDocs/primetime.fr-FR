---
description: Outre les paramètres de requête de base, les paramètres de requête facultatifs permettent au serveur de manifeste de fonctionner avec différents clients et situations.
seo-description: Outre les paramètres de requête de base, les paramètres de requête facultatifs permettent au serveur de manifeste de fonctionner avec différents clients et situations.
seo-title: Paramètres de requête facultatifs par client et situation
title: Paramètres de requête facultatifs par client et situation
uuid: e3fae41e-9f7d-4f01-9a01-52a1d5f5dad5
translation-type: tm+mt
source-git-commit: ''

---


# Paramètres de requête facultatifs par client et situation {#optional-query-parameters-by-client-and-situation}

Outre les paramètres de requête de base, les paramètres de requête facultatifs permettent au serveur de manifeste de fonctionner avec différents clients et situations.

## Insertion d’une publicité avec Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}

Sur le réseau CDN (Content diffusion Network) d’Akamai, le serveur Edge d’Akamai fonctionne comme un intermédiaire entre le client et le serveur de manifeste. Si vous utilisez également Ad Scaler, les paramètres `ptassetid` et de `live` requête fournissent les informations requises à Akamai Edge.

Le `ptassetid` paramètre correspond à l’identifiant de l’éditeur pour sa ressource. Akamai l’utilise, plutôt que l’URL codée en base 64 que vous fournissez dans le cadre de l’URL de demande, pour identifier la liste de lecture à fournir au serveur de manifeste pour l’insertion d’annonces.

Le `live` paramètre fait la distinction entre le contenu en direct et la vidéo à la demande (VOD). Le serveur de manifeste a besoin de ces informations pour prendre en charge son interface rationalisée avec Akamai.

Voici un exemple d’URL présentant les paramètres relatifs à Akamai :

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## Insertion de publicité à partir de TVSDK sur Xbox {#section_5DB405F4647240A0B83E72DE35D5EC80}

Un lecteur basé sur Primetime TVSDK sur Xbox n&#39;a pas besoin de fournir des paramètres de requête supplémentaires au-delà des paramètres de base.

## Insertion d’une publicité à partir de TVSDK sur iOS avec Safari {#section_250E493A125E4F82940D19C7DA2AAB2E}

Un lecteur basé sur Primetime TVSDK sur iOS utilisant le navigateur Safari doit spécifier les paramètres `ptplayer` et `live` les paramètres en plus des paramètres de requête de base.

Le serveur de manifeste reconnaît la `ptplayer` valeur `ios-mobileweb` et élimine le pré-roll du manifeste assemblé par publicité qu’il renvoie.

Le `live` paramètre indique au serveur de manifeste s’il doit renvoyer du contenu actif ou VOD.

Voici un exemple d’URL présentant les paramètres relatifs à iOS avec Safari :

```
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## Insertion d’une publicité à l’aide d’un format de indice publicitaire personnalisé {#section_82AF880AAABE4BD4B593D906434D4D89}

Adobe fournit des noms pour les formats de indices publicitaires qu’il ne prend pas directement en charge dans le pack Primetime. Pour utiliser un tel format, indiquez son nom fourni par Adobe comme valeur du `ptcueformat` paramètre.

Voici un exemple d’URL spécifiant un format de indice publicitaire personnalisé :

```
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## Insertion d’annonces à l’aide d’indices publicitaires pour créer une chronologie FreeWheel pour VOD {#section_E0D830F5EEE24639819B975B90F6999F}

Pour que le contenu VOD contenant des indices publicitaires soit analysé et inclus dans une demande de publicité FreeWheel, définissez la valeur du `ptcueformat` paramètre sur `DPIsimple`.

Voici un exemple d’URL qui spécifie l’utilisation d’une chronologie FreeWheel pour VOD :

```
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## Insertion d’une publicité à l’aide d’une chronologie personnalisée pour VOD {#section_F398F7659164463FA886A4CC787C7B5A}

Pour demander au serveur de manifeste d’insérer des publicités dans le contenu VOD selon un planning que vous fournissez, définissez la valeur du `pttimeline` paramètre sur une chaîne spécifiant le calendrier. Voir le format de chronologie [VOD](../../msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)

Voici un exemple d’URL qui utilise une chronologie personnalisée pour VOD :

```
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

Il spécifie une coupure initiale d’une minute contenant jusqu’à deux publicités, suivie d’un segment de contenu de deux minutes, suivi d’une coupure de 30 secondes contenant jusqu’à deux publicités, suivie d’un segment de contenu de cinq minutes.

L’assemblage de publicités pour une chronologie de contenu personnalisé pour le contenu VOD se comporte comme suit :

* La publicité s’affiche à la limite de coupure la plus proche après l’heure de placement de la publicité spécifiée par le serveur d’annonces.
* Les segments durent au moins deux secondes.

## Autorisation de segments TS {#section_BF855A4399DC42CB8C0586113A416BBC}

Adobe ne prend en charge cette fonctionnalité que pour le réseau de diffusion de contenu Akamai. La diffusion en flux continu en direct HTTP (HLS) fournit des segments de flux de transport (TS) à l’aide d’une liste de lecture au niveau du flux M3U8. Plusieurs playlists au niveau du flux sont fournies au client dans une variante de playlist M3U8. Le client sélectionne un flux de liste de lecture à partir de la liste de variante, puis télécharge les segments TS dans cette liste de lecture au niveau du flux un par un. En fonctionnement normal, le contenu demandé peut nécessiter l&#39;autorisation de cookie, que le serveur de manifeste gère de manière invisible en arrière-plan. Il extrait le cookie du contenu brut et ajoute un jeton approprié à l’URL à utiliser pour demander le flux de la liste de lecture sélectionnée.

Lorsque les paramètres de requête d’URL d’amorçage sont inclus `pttoken=true`, l’éditeur a besoin d’un cookie pour demander chaque segment TS, plutôt qu’une seule fois pour l’ensemble du flux. Le serveur de manifeste associe ce cookie en tant que paramètre de requête à chaque URL de segment TS dans la liste de lecture de flux qu’il renvoie.
