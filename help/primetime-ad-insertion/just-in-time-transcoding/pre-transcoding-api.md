---
title: API de prétranscodage
description: Vous pouvez utiliser l’API de reconditionnement juste à temps pour transcoder les créatifs publicitaires à l’avance. Dès lors, des versions compatibles avec le contenu sont disponibles si nécessaire, ce qui élimine le délai de 2 à 4 minutes associé au reconditionnement juste à temps (JIT).
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# API de prétranscodage et de reconditionnement {#pre-transcoding-api}

Primetime Ad Insertion propose une API de prétranscodage dans les cas où les URL de création sont connues à l’avance, comme pour les événements de grande taille vendus directement.  Cela élimine le délai de 2 à 4 minutes associé au transcodage juste à temps.

## Requête HTTP {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Envoyez une commande de POST HTTP à l’URL spécifiée pour indiquer à CRS la publicité que vous souhaitez transcodée et les options que vous souhaitez qu’elle utilise. Le code de réponse signale un succès ou un échec, ainsi que d’autres informations.

Cette requête nécessite un nom d’utilisateur et un mot de passe. Vous pouvez les obtenir auprès de votre gestionnaire de compte technique Adobe. Si vous avez besoin d’informations sur l’authentification, contactez votre représentant d’activation Adobe Primetime.

Pour envoyer une requête de transcodage à CRS, envoyez un message HTTP comme suit :

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

La variable `RepackageList` dans le corps peut contenir entre 1 et 300 `Repackage` blocs. Si le nombre de `Repackage` Les blocs du corps dépassent 300, alors la requête HTTP échoue avec l’erreur suivante :

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


Les paramètres obligatoires et facultatifs d’une `Repackage` block sont les suivantes :

* **`AdSystem`** (Obligatoire) - Le serveur de publicités source, par exemple : `Auditude`, `FreeWheel`, `Apad.tv`. Il s’agit d’une valeur string qui correspond à l’élément VAST . `AdSystem`.

* **`AdId`** (Obligatoire) : identifiant du serveur d’annonces tiers spécifié dans la requête. Il correspond au `id` de l’attribut `Ad` dans une réponse VAST.

* **`CreativeURL`** (Obligatoire) - L’emplacement (URI) de l’élément créatif publicitaire à transcoder. Cela correspond au VAST `MediaFile` élément .

* `CreativeID` (facultatif) - Identifiant de l’élément créatif publicitaire à inclure dans l’expérience publicitaire.
* **`Zone`** (Obligatoire) - ID de zone pour votre compte (procurez-vous l’aide de votre gestionnaire de compte technique). Il s’agit d’une valeur numérique qui correspond à la plateforme Auditude. `publisher_site_id` .

* **`Format`** (facultatif) - Paramètres permettant de contrôler la manière dont CRS transcode le contenu créatif publicitaire :

   * `clientside` - Générer une sortie compatible avec l’URL utilisée par TVSDK pour communiquer avec le réseau de diffusion de contenu.

  >[!IMPORTANT]
  >
  >Vous devez fournir ce paramètre si vous souhaitez que la publicité reconditionnée soit compatible avec l’Ad Insertion côté client. Si vous ne fournissez pas cette information, la publicité reconditionnée sera uniquement compatible avec l’Ad Insertion côté serveur.

   * `hls` - Générez un contenu publicitaire transcodé compatible HLS.
   * `dash` - Générez un contenu publicitaire transcodé compatible avec DASH.
   * `id3` : injectez des balises de métadonnées minutées ID3 dans le contenu publicitaire transcodé.
   * `targetdur` - Durée du segment (en secondes) pour le créatif publicitaire transcodé. Par défaut : `targetdur=4`. Cette valeur doit correspondre à la valeur spécifiée dans le manifeste pour `<s>` dans la balise de durée de la cible : `#EXT-X-TARGETDURATION:<s>`.

  >[!NOTE]
  >
  >Les ressources compatibles avec DASH ne sont pas compatibles avec l’insertion de publicités Adobe Primetime.

>[!IMPORTANT]
>
>Pour garantir une lecture plus fluide, définissez `targetdur` pour correspondre à la durée du bloc de contenu.

## Réponse HTTP {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRS répond à la demande avec l’un des codes d’état suivants :

* **HTTP 202** - Acceptée (avec corps vide). Cela indique la réussite. CRS télécharge la publicité transcodée sur le serveur CDN.
* **HTTP 400** - Requête incorrecte. Le code XML publié n’est pas valide.
* **HTTP 500** - Erreur interne du serveur. Le serveur a rencontré un problème interne (par exemple, le serveur n&#39;a pas pu se connecter à une base de données).

## Pré-transcodage des ressources pour SSAI ou CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

À l’aide de l’API de reconditionnement, vous pouvez précoder les futurs événements SSAI ou CSAI. Si les ressources sont destinées à être utilisées avec l’interface d’interface utilisateur (SSAI) à l’avenir, assurez-vous que tous les paramètres des appels du POST sont uniques. Les paramètres sont : AdSystem, AdId, CreativeURL, Zone, Format. Toutes les différences dans cet ensemble de paramètres entraînent une nouvelle requête de transcodage pour l’interface utilisateur unique.

Pour les ressources utilisées avec CSAI à l’avenir, l’unicité des ressources dépend de Zone et de CreativeURL. AdSystem et AdId ne génèrent pas de ressources transcodées différentes et elles sont disponibles pour les clients.
