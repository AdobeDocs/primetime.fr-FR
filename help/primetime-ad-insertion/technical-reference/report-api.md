---
title: API de rapport
description: API de rapport Auditude
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 1%

---

# API de rapport {#report-api}

L’interface utilisateur dispose de rôles gérés pour les clients et pour l’équipe d’activation (Adobe). Les clients peuvent accéder au portail, puis créer et modifier leurs configurations. Ils peuvent également consulter les rapports pour connaître les impressions publicitaires de l’interface utilisateur.

Les API fonctionnent en arrière-plan pour faciliter la communication entre les clients et les administrateurs et l’infrastructure principale.

Pour explorer le [!DNL Primetime Ad Insertion] APIs voir [Points de terminaison de l’API Ad Insertion dans l’interface utilisateur basculée](https://adconfigservice-va6.cloud.adobe.io/swagger-ui/index.html#/).

## Point d’entrée API {#report-api-endpoint}

### Production {#production}

`https://dai-primetime.adobe.io/report`

### Sandbox {#sandbox}

`https://dai-sandbox1-primetime.adobe.io/report`

## Paramètres de requête


| Nom | Significativité | Type de valeur | Obligatoire ? | Valeur par défaut | Contrainte | Exemple/Valeurs d’exemple valides |
|----------|-----------------------------------------------------------------------------------------------|----------------|----------------|---------------------|------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| endDate | Date de fin des données du rapport | date | Y | AUCUN | pas plus récent qu’hier en UTC-8 | ######## |
| filtres | filtrer sur une ou plusieurs colonnes | string | N | AUCUN | ad_config_id , zone_id | ad_config_id=990,900;state=active |
|          |                                                                                               |                |                |                     | Lorsque metaData est défini sur &quot;true&quot; dans la requête, vous pouvez également filtrer par nom. |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Plusieurs clés de filtre sont séparées par des points-virgules. |
|          |                                                                                               |                |                |                     |                                                                                    | Utiliser des valeurs séparées par des virgules pour fournir une liste de valeurs pour la clé de filtre |
| groupBy | Regroupez par heure d’activation (année \| mois \| jour) ou ad_config_id. Adconfig est synonyme d’AdRule. | string | N | AUCUN | y \| m \| d , ad_config_id | m , ad_config_id |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |
|          |                                                                                               |                |                |                     |                                                                                    | Pour groupBy à l’heure, indiquez l’une des valeurs y ou m ou d |
|          |                                                                                               |                |                |                     |                                                                                    |                                                                         |



## En-têtes {#headers}

| Nom | Type de valeur | Obligatoire | Exemple de valeur | Significativité |
|-----------------------|----------------|---------------|-------------------------------------|------------------------------------|
| Accepter | string | Y | text/csv pour CSV | Type de réponse attendue de l’API |
|                       |                |               | application/json ou &#39;*/*&#39; pour JSON |                                    |
| Jeton d’autorisation | string | Y | xyz | jeton d’autorisation |
| x-api-key | string | Y | xyz | Clé API |
| x-gw-ims-org-id | string | Y | xyz12345 | ID d’organisation IMS de votre compte |

* Vous pouvez générer le jeton d’autorisation (également appelé jeton d’accès) en suivant les étapes présentées dans la page d’aide sur l’authentification JWT d’Adobe.io.
  >>
  [!NOTE]
  >Le jeton d’autorisation expire après 24 heures. Ainsi, si vous utilisez l’API de rapport avec un script récurrent, veillez à générer le jeton d’authentification avant son expiration ou lorsque vous obtenez une erreur Oauth indiquant que le jeton n’est pas valide.

* Pour définir les valeurs correctes dans l’en-tête de la requête et générer un jeton d’autorisation (à l’aide de l’authentification JWT), vous devez connaître les configurations suivantes pour votre compte. Contactez l’équipe d’assistance de Primetime pour obtenir ces valeurs.
Identifiant du compte technique

   * ID d’organisation
   * Api_key
   * Client_secret

## Sortie {#output}

Par défaut, le résultat de la requête de l’API de rapport est au format JSON qui spécifie les impressions par rapport aux différentes valeurs des dimensions (paramètre groupby) demandées. Voici un exemple de sortie :

```JSON
[
    {
        "dates": "07-2020",
        "total_impressions": 213007041
    },
    {
        "dates": "08-2020",
        "total_impressions": 174711626
    },
    {
        "dates": "09-2020",
        "total_impressions": 102863153
    }
]
```

## Codes et chaînes d’erreur {#error-codes-strings}

### Format de réponse d’erreur {#error-response-format}

Erreur de rendu de la macro &#39;code&#39; : valeur non valide spécifiée pour le paramètre `com.atlassian.confluence.ext.code.render.InvalidValueException`

```Shell
{
"error_code": "<ERROR_CODE>",
"message": "<ERROR_MESSAGE>"
}
```

Le tableau ci-dessous répertorie les codes d’erreur et les messages que l’API de rapport peut renvoyer. Pour les erreurs liées à la couche d’autorisation, reportez-vous à la section [documentation du code d’erreur](https://experienceleague.adobe.com/docs/experience-platform/landing/troubleshooting.html?lang=en#errors-and-troubleshooting) de Adobe.io.

| Code d’erreur | Message d’erreur |
|-----------------------|------------------------------------------|
| 4001007 | Le détail de l’utilisateur n’est pas valide. |
| 4001008 | Toutes les zones ne proviennent pas du même compte. |
| 5001010 | Une erreur interne s’est produite. |
| 4001011 | Les dates ne sont pas envoyées au format requis. |
| 4001012 | Les dates sont hors plage. |
| 4001013 | Le paramètre obligatoire est manquant. |
| 4001014 | La liste de zones est vide pour le compte. |
| 4001015 | Clés de filtre non valides dans la requête. |
| 4001016 | Option GroupBy non valide dans la requête. |
| 4001017 | ID non valide fourni dans la requête |

## Exemples d’appels et résultats attendus {#sample-calls-expected-results}

Voici la commande curl pour obtenir le nombre d’impressions mensuel entre 2020-07-01 et 2021-06-30 à l’aide du jeton d’accès :

**Exemple d’appel API de création de rapports**

```shell
curl --location --request GET 'https://dai-sandbox1-primetime.adobe.io/report?startDate=2020-07-01&endDate=2021-06-30&groupBy=m&unpaged=true' \
--header 'x-api-key: <API_KEY>' \
--header 'x-gw-ims-org-id: <ORG_ID>' \
--header 'Authorization: Bearer <ACCESS_TOKEN_STRING>' \
--header 'Accept: application/json'
```

| Exemple d’appel/cas d’utilisation | Résultat attendu |
|---|---|
| Récupérer le rapport avec les GET de dates de début et de fin : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2021-01-01 header : Accepter = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant à ce compte total_impressions |
| Récupérer le rapport avec GroupBy = d \| m \| y GET : [API_ENDPOINT]//report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d \| m \| y header : Accepter = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant aux dates de ce compte (jj-mm-aaaa \| mm-aaaa \| format aaaa) total_impressions |
| Récupérer le rapport avec GroupBy = ad_config_id GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=ad_config_id header : Acceptez = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant à ce compte ad_config_id total_impressions |
| Récupérer le rapport avec GroupBy = d \| m \| y et ad_config_id GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d,ad_config_id header : Accepter = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant à ce compte ad_config_id dates (mm-jj-aaaa \| mm-aaaa \| format aaaa) total_impressions |
| Récupérer le rapport avec metaData=true et groupBy=d \| m \| y GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=ad_config_id header : Accept = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant à ce compte ad_config_id name total_impressions |
| Récupérer le rapport avec groupBy=d \| m \| y et ad_config_id GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=d \| m \| y,ad_config_id header : Accepter = application/json. ou */* | Json avec les paramètres suivants avec toutes les publicités appartenant à ce compte ad_config_id nom total_impressions dates (mm-jj-aaaa \| mm-aaaa \| format aaaa) |
| Récupérer le rapport pour obtenir toutes les lignes pour une période donnée (avec unpaged = true) GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;groupBy=d&amp;unpaged=true | 31 entrées dans le tableau Json renvoyé |
| Récupérer le rapport avec des paramètres de requête de page valides GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;page=0&amp;size=5&amp;groupBy=d | 5 entrées dans le tableau renvoyé |
| Récupérer le rapport, avec GET au format csv : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10 header : Accept = text/csv | Une chaîne CSV est renvoyée, avec l’en-tête : total_impressions |
| Récupérer le rapport, avec le format csv et groupBy = d \| m \| y GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;groupBy=d\|m\|y header : Accept = text/csv | Une chaîne CSV est renvoyée, avec l’en-tête : dates total_impressions (jj-mm-aaaa \| mm-aaaa \| format aaaa). |
| Récupérer le rapport, avec le format csv et les métadonnées = GET true : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true header : Accepter = text/csv | Une chaîne CSV est renvoyée, avec l’en-tête : total_impressions |
| Récupérer le rapport, avec le format csv , les métadonnées = true et groupBy = d \| m \| y GET : [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true&amp;groupBy=d\|m\|y header : Accept = text/csv | Une chaîne CSV est renvoyée, avec l’en-tête : dates total_impressions (jj-mm-aaaa \| mm-aaaa \| format aaaa). |


## Stratégie de limitation de l’API de rapport {#report-api-throttling-policy}

* 5 demandes d’API sont autorisées pendant une fenêtre de 5 secondes pour chaque utilisateur.
* Si un utilisateur dépasse la limite, la réponse est retardée de 5 secondes.
* Si un utilisateur effectue plus de 10 appels dans une fenêtre de 5 secondes, il commence à être rejeté avec la réponse &quot;429 Too many requests&quot;.
