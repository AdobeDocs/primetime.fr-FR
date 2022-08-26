---
title: Métadonnées utilisateur
description: Métadonnées utilisateur
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Métadonnées utilisateur {#user-metadata}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Points de terminaison de l’API REST {#clientless-endpoints}

&lt;reggie_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## Description {#description}

Récupérez les métadonnées que MVPD a partagées à propos de l’utilisateur authentifié.

<div>


| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/usermetadata | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur</br>2.  deviceId (obligatoire)</br>3.  device_info/X-Device-Info (obligatoire)</br>4.  deviceType</br>5.  deviceUser (obsolète)</br>6.  appId (obsolète) | GET | XML ou JSON contenant des métadonnées utilisateur ou des détails d’erreur en cas d’échec. | 200 - Succès</br></br>404 - Aucune métadonnée trouvée</br></br>412 - Jeton AuthN non valide (par exemple, jeton expiré) |


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: Cela peut être transmis device_info comme paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, il doit être transmis sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section [Transmission des informations de périphérique et de connexion](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>Si ce paramètre est correctement défini, ESM propose des mesures qui sont [ventilation par type d’appareil](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Remarque**: device_info remplace ce paramètre. |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil.</br></br>**Remarque**: s’il est utilisé, deviceUser doit avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/registration-code-request) requête. |
| _appId_ | ID/nom de l’application. </br></br>**Remarque**: device_info remplace ce paramètre. Si utilisé, `appId` doivent avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) requête. |

>[!NOTE]
> 
>Les informations de métadonnées utilisateur doivent être disponibles une fois le flux d’authentification terminé, mais peuvent être mises à jour sur le flux d’autorisation, en fonction du MVPD et du type de métadonnées.

</br>

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

 

À la racine de l’objet, trois noeuds sont disponibles :

* *mis à jour*: spécifie un horodatage UNIX qui représente la dernière fois où les métadonnées ont été mises à jour. Cette propriété est définie initialement par le serveur lors de la génération des métadonnées pendant la phase d’authentification. Les appels suivants (une fois les métadonnées mises à jour) génèrent un horodatage incrémenté.

* *data*: contient les valeurs réelles des métadonnées. 

* *encrypted*: un tableau répertoriant les propriétés chiffrées. Pour déchiffrer une valeur de métadonnées spécifique, le programmeur doit effectuer un décodage Base64 sur les métadonnées, puis appliquer un déchiffrement RSA sur la valeur obtenue, en utilisant sa propre clé privée (l’Adobe chiffre les métadonnées sur le serveur à l’aide du certificat public du programmeur).

En cas d’erreur, le serveur renvoie un objet XML ou JSON spécifiant un message d’erreur détaillé.

**En savoir plus :** [Métadonnées utilisateur](http://tve.helpdocsonline.com/user-metadata-v2)


### [Retour à la référence de l’API REST](http://tve.helpdocsonline.com/rest-api-reference)
