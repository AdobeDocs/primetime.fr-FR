---
title: Métadonnées utilisateur
description: Métadonnées utilisateur
exl-id: 3d7b6429-972f-4ccb-80fd-a99870a02f65
source-git-commit: 6779e20e37f1396402f36564e2c85d48d8c581a3
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Métadonnées utilisateur {#user-metadata}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Points de terminaison de l’API REST {#clientless-endpoints}

&lt;reggie_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Description {#description}

Récupérez les métadonnées que MVPD a partagées à propos de l’utilisateur authentifié.


| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/usermetadata | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur</br>2.  deviceId (obligatoire)</br>3.  device_info/X-Device-Info (obligatoire)</br>4.  deviceType</br>5.  deviceUser (obsolète)</br>6.  appId (obsolète) | GET | XML ou JSON contenant des métadonnées utilisateur ou des détails d’erreur en cas d’échec. | 200 - Succès</br></br>404 - Aucune métadonnée trouvée</br></br>412 - Jeton AuthN non valide (par exemple, jeton expiré) |


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: cette variable peut être transmise à device_info en tant que paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, elle doit être transmise sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section **Transmission des informations de périphérique et de connexion** <!--http://tve.helpdocsonline.com/passing-device-information-->. |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>Si ce paramètre est correctement défini, ESM propose des mesures qui sont [ventilation par type d’appareil](/help/authentication/entitlement-service-monitoring-overview.md#progr-filter-metrics) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.</br></br>Voir [Avantages de l’utilisation d’un paramètre de type d’appareil sans client dans Pass etrics ](/help/authentication/benefits-of-using-the-clientless-devicetype-parameter-in-pass-metrics.md)</br></br>**Remarque :** La variable `device_info` remplace ce paramètre. </br> |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil.</br></br>**Remarque :**En cas d’utilisation, `deviceUser` doivent avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](/help/authentication/registration-code-request.md) requête. |
| _appId_ | ID/nom de l’application. </br></br>**Remarque :**Le `device_info` remplace ce paramètre. En cas d’utilisation, `appId` doivent avoir les mêmes valeurs que dans la variable **Créer un code d’enregistrement** requête. |

>[!NOTE]
> 
>Les informations de métadonnées utilisateur doivent être disponibles une fois le flux d’authentification terminé, mais peuvent être mises à jour sur le flux d’autorisation, en fonction du MVPD et du type de métadonnées.




## Exemple de réponse {#sample-response}

Après un appel réussi, le serveur répond avec un objet XML (par défaut) ou JSON avec une structure similaire à celle présentée ci-dessous :

```JSON
    {
        updated: 1334243471,
        encrypted: ["encryptedProp"],
        data: {
              zip: ["12345", "34567"],
              maxRating: { 
                  "MPAA": "PG-13",
                  "VCHIP": "TV-Y", 
                  "URL": "http://exam.pl/e/manage/ratings"
              },
              householdID: "3456",
              userID: "BgSdasfsdk23/dsaf3+saASesadgfsShggssd=",
              channelID: ["channel-1", "channel-2"]
    }
```

À la racine de l’objet, il y a trois noeuds :

* **mis à jour**: spécifie un horodatage UNIX qui représente la dernière fois où les métadonnées ont été mises à jour. Cette propriété est définie initialement par le serveur lors de la génération des métadonnées pendant la phase d’authentification. Les appels suivants (une fois les métadonnées mises à jour) génèrent un horodatage incrémenté.

* **data**: contient les valeurs réelles des métadonnées.

* **encrypted**: un tableau répertoriant les propriétés chiffrées. Pour déchiffrer une valeur de métadonnées spécifique, le programmeur doit effectuer un décodage Base64 sur les métadonnées, puis appliquer un déchiffrement RSA sur la valeur obtenue, en utilisant sa propre clé privée (l’Adobe chiffre les métadonnées sur le serveur à l’aide du certificat public du programmeur).

En cas d’erreur, le serveur renvoie un objet XML ou JSON spécifiant un message d’erreur détaillé.

Pour plus d’informations, voir [Métadonnées utilisateur](/help/authentication/user-metadata-feature.md).

### [Retour à la référence de l’API REST](/help/authentication/rest-api-reference.md).
