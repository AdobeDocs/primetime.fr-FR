---
title: API de prétranscodage
description: Vous pouvez utiliser l’API de reconditionnement juste à temps pour transcoder les éléments créatifs à l’avance, de sorte qu’une version compatible avec le contenu soit disponible si nécessaire, éliminant ainsi le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).
seo-description: Vous pouvez utiliser l’API de reconditionnement juste à temps pour transcoder les éléments créatifs à l’avance, de sorte qu’une version compatible avec le contenu soit disponible si nécessaire, éliminant ainsi le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).
seo-title: API de prétranscodage
uuid: 03cd2428-510a-4b99-8496-059a48d5abba
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# API de prétranscodage et de reconditionnement {#pre-transcoding-api}

L’Ad Insertion Primetime offre une API de prétranscodage pour les cas où les URL créatives sont connues à l’avance, par exemple pour les événements à vente directe volumineux.  Cela élimine le délai de 2 à 4 minutes associé au transcodage juste à temps.

## Requête HTTP {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Envoyez une commande de POST HTTP à l’URL spécifiée pour indiquer à CRS la publicité que vous souhaitez transcoder et les options que vous souhaitez qu’elle utilise. Le code de réponse signale la réussite ou l’échec et d’autres informations.

Cette demande nécessite un nom d’utilisateur et un mot de passe. Vous pouvez les obtenir auprès de votre gestionnaire de compte technique Adobe. Si vous avez besoin d’informations sur l’authentification, contactez votre représentant Adobe Primetime Enablement.

Pour envoyer une demande de transcodage à CRS, envoyez un message HTTP comme suit :

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **Méthode -** `POST`

* **Auth -** `Digest`

* **En-tête -** `Content-Type: text/xml`

* **Body -** XML comme dans l’exemple suivant :

   ```xml
   <RepackageList>
       <Repackage>
           <AdSystem>Auditude</AdSystem>
           <AdID>AUD1</AdID>
           <CreativeID>AUD-CR1</CreativeID>
           <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
           <Zone>3</Zone>
       </Repackage>
       <Repackage>
           <AdSystem>Auditude</AdSystem>
           <AdID>AUD2</AdID>
           <CreativeID>AUD-CR1</CreativeID>
           <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
           <Format>id3 targetdur=5</Format>
           <Zone>3</Zone>
       </Repackage>
   </RepackageList>
   ```

Le bloc `RepackageList` dans le corps peut contenir de 1 à 300 blocs `Repackage`. Si le nombre de blocs `Repackage` dans le corps dépasse 300, la requête HTTP échoue avec l&#39;erreur suivante :

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


Les paramètres requis et facultatifs d&#39;un bloc `Repackage` sont les suivants :

* **`AdSystem`** (Obligatoire) - Serveur d&#39;annonces source, par exemple,  `Auditude`,  `FreeWheel`,  `Apad.tv`. Il s&#39;agit d&#39;une valeur de chaîne qui correspond à l&#39;élément VAST `AdSystem`.

* **`AdId`** (Obligatoire) : identifiant du serveur publicitaire tiers spécifié dans la requête. Il correspond à l&#39;attribut `id` de l&#39;élément `Ad` dans une réponse VAST.

* **`CreativeURL`** (Obligatoire) - Emplacement (URI) de l’élément créatif publicitaire à transcoder. Cela correspond à l&#39;élément VAST `MediaFile`.

* `CreativeID` (facultatif) - Identifiant de l’élément créatif publicitaire à inclure dans l’expérience publicitaire.
* **`Zone`** (Obligatoire) - ID de zone pour votre compte (obtenir auprès de votre gestionnaire de compte technique). Il s’agit d’une valeur numérique qui correspond au paramètre de plate-forme Auditude `publisher_site_id`.

* **`Format`** (Facultatif) - Paramètres permettant de contrôler la manière dont CRS transcode la création publicitaire :

   * `clientside` - Générer une sortie compatible avec l’URL utilisée par TVSDK pour communiquer avec le CDN.
   >[!IMPORTANT]
   >
   >Vous devez fournir ce paramètre si vous souhaitez que la publicité reconditionnée soit compatible avec l’Ad Insertion côté client. Si vous ne fournissez pas cette information, la publicité reconditionnée sera uniquement compatible avec l’Ad Insertion côté serveur.

   * `hls` - Générer un élément créatif publicitaire transcodé compatible HLS.
   * `dash` - Générer un élément créatif publicitaire transcodé compatible DASH.
   * `id3` - Injecter des balises de métadonnées minutées ID3 dans la publicité publicitaire transcodée créative.
   * `targetdur` - Durée du segment (en secondes) pour l’élément créatif publicitaire transcodé. La valeur par défaut est `targetdur=4`. Cette valeur doit correspondre à la valeur spécifiée dans le manifeste pour `<s>` dans la balise de durée de la cible : `#EXT-X-TARGETDURATION:<s>`.

   >[!NOTE]
   >
   >Les ressources compatibles avec DASH ne sont pas compatibles avec l’insertion d’annonces Adobe Primetime.

>[!IMPORTANT]
>
>Pour une lecture plus fluide, définissez `targetdur` sur la durée du bloc de contenu.

## Réponse HTTP {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

Le CS Ex répond à la demande en utilisant l&#39;un des codes d&#39;état suivants :

* **HTTP 202** - Accepté (avec corps vide). Cela indique la réussite. CRS télécharge la publicité transcodée sur le serveur CDN.
* **HTTP 400**  - Requête incorrecte. Le code XML publié n&#39;est pas valide.
* **HTTP 500**  - Erreur interne du serveur. Le serveur a rencontré un problème interne (par exemple, le serveur n&#39;a pas pu se connecter à une base de données).

## Pré-transcodage des fichiers pour SSAI ou CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

A l’aide de l’API de reconditionnement, vous pouvez prétranscoder de futurs événements SSAI ou CSAI. Si les ressources sont destinées à être utilisées avec SSAI à l’avenir, veillez à ce que tous les paramètres des appels du POST soient uniques. Les paramètres sont les suivants : AdSystem, AdId, CreativeURL, Zone, Format. Toute différence dans cet ensemble de paramètres entraîne une nouvelle demande de transcodage pour SSAI.

Pour les ressources utilisées avec CSAI à l’avenir, l’unicité des ressources dépend de Zone et de CreativeURL. AdSystem et AdId ne génèrent pas de fichiers transcodés différents et sont disponibles pour les clients.