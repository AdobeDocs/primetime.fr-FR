---
description: Vous pouvez utiliser l’API de reconditionnement CRS pour transcoder à l’avance les éléments créatifs et non-HLS. Une version HLS est donc disponible lorsque vous devez l’exécuter, éliminant ainsi le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).
seo-description: Vous pouvez utiliser l’API de reconditionnement CRS pour transcoder à l’avance les éléments créatifs et non-HLS. Une version HLS est donc disponible lorsque vous devez l’exécuter, éliminant ainsi le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).
seo-title: API de reconditionnement
title: API de reconditionnement
uuid: 03cd2428-510a-4b99-8496-059a48d5abba
translation-type: tm+mt
source-git-commit: 5c026bfc678bafc08f93ad056823e36fd77a8a25

---


# API de reconditionnement {#repackaging-api}

Vous pouvez utiliser l’API de reconditionnement CRS pour transcoder à l’avance les éléments créatifs et non-HLS. Une version HLS est donc disponible lorsque vous devez l’exécuter, éliminant ainsi le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).

## Requête HTTP {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Envoyez une commande HTTP POST à l’URL spécifiée pour indiquer à CRS quel créatif publicitaire vous souhaitez transcoder et quelles options vous souhaitez qu’il utilise. Le code de réponse signale la réussite ou l’échec et d’autres informations.

Cette demande nécessite un nom d’utilisateur et un mot de passe. Vous pouvez les obtenir auprès de votre gestionnaire de compte technique Adobe. Si vous avez besoin d’informations sur l’authentification, contactez votre représentant Adobe Primetime Enablement.

Pour envoyer une demande de transcodage à CRS, envoyez un message HTTP comme suit :

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **Méthode -**`POST`

* **Auth -**`Digest`

* **En-tête -**`Content-Type: text/xml`

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

Le `RepackageList` bloc du corps peut contenir de 1 à 300 `Repackage` blocs. Si le nombre de `Repackage` blocs dans le corps dépasse 300, la requête HTTP échoue avec l’erreur suivante :

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


Les paramètres obligatoires et facultatifs d’un `Repackage` bloc sont les suivants :

* **`AdSystem`** (Obligatoire) - Serveur d&#39;annonces source, par exemple `Auditude`, `FreeWheel`, `Apad.tv`. Il s’agit d’une valeur de chaîne qui correspond à l’élément VAST `AdSystem`.

* **`AdId`** (Obligatoire) : identifiant du serveur d’annonces tiers spécifié dans la requête. Il correspond à l’ `id` attribut de l’ `Ad` élément dans une réponse VAST.

* **`CreativeURL`** (Obligatoire) - Emplacement (URI) de l’élément créatif publicitaire à transcoder. Cela correspond à l’ `MediaFile` élément VAST.

* `CreativeID` (facultatif) - Identifiant du créatif publicitaire à inclure dans le cadre de l’expérience publicitaire.
* **`Zone`** (Obligatoire) - ID de zone pour votre compte (auprès de votre gestionnaire de compte technique). Il s’agit d’une valeur numérique qui correspond au paramètre de plate-forme Auditude `publisher_site_id` .

* **`Format`** (Facultatif) - Paramètres permettant de contrôler la manière dont CRS transcode le contenu créatif de la publicité :

   * `clientside` - Générer une sortie compatible avec l’URL utilisée par TVSDK pour communiquer avec le CDN.
   >[!IMPORTANT]
   >
   >Vous devez fournir ce paramètre si vous souhaitez que la publicité reconditionnée soit compatible avec l’insertion d’annonce côté client. Si vous ne fournissez pas cette information, la publicité reconditionnée sera uniquement compatible avec l’insertion d’annonces côté serveur.

   * `hls` - Générer un élément créatif publicitaire transcodé compatible HLS.
   * `dash` - Générer un élément créatif publicitaire transcodé compatible DASH.
   * `id3` - Injectez des balises de métadonnées minutées ID3 dans le fichier de création publicitaire transcodé.
   * `targetdur` - Durée du segment (en secondes) pour le créatif publicitaire transcodé. La valeur par défaut est `targetdur=4`. Cette valeur doit correspondre à la valeur spécifiée dans le manifeste pour `<s>` la balise de durée  du : `#EXT-X-TARGETDURATION:<s>`.
   >[!NOTE]
   >
   >Les fichiers compatibles DASH ne sont pas compatibles avec l’insertion d’annonces Adobe Primetime.

>[!IMPORTANT]
>
>Pour une lecture plus fluide, définissez cette option `targetdur` pour qu’elle corresponde à la durée du fragment de contenu.

## Réponse HTTP {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

Le CS Ex répond à la demande avec l’un des codes d’état suivants :

* **HTTP 202** - Accepté (avec corps vide). Cela indique la réussite. CRS télécharge la publicité transcodée sur le serveur CDN.
* **HTTP 400** - Requête incorrecte. Le code XML publié n&#39;est pas valide.
* **HTTP 500** - Erreur interne du serveur. Le serveur a rencontré un problème interne (par exemple, le serveur n’a pas pu se connecter à une base de données).

## Pré-transcodage des fichiers pour SSAI ou CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

Grâce à l’API de reconditionnement, vous pouvez précoder les futurs  SSAI ou CSAI. Si les ressources sont destinées à être utilisées avec SSAI à l’avenir, assurez-vous que tous les paramètres des appels POST sont uniques. Les paramètres sont les suivants : AdSystem, AdId, CreativeURL, Zone, Format. Toute différence dans cet ensemble de paramètres entraîne une nouvelle demande de transcodage pour SSAI.

Pour les ressources utilisées avec CSAI à l’avenir, l’unicité des ressources dépend de Zone et de CreativeURL. AdSystem et AdId ne génèrent pas de fichiers transcodés différents et sont disponibles pour les clients.
