---
seo-title: Détails du processus de stratégie
title: Détails du processus de stratégie
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Processus BEES {#bees-workflow}

**Résumé :**

* **Stratégie** - Créez une stratégie DRM pour les abeilles qui indique que les abeilles sont requises pour tout le contenu assemblé à l’aide de cette stratégie.
* **Packaging** - Empaquetage de contenu à l’aide de la stratégie DRM basée sur les BEES.
* **Authentification** : authentifiez votre périphérique client et utilisez l’API DRM Primetime, ou l’API Primetime, pour associer ce jeton à la DRM de Primetime Cloud. Ce faisant, le périphérique client enverra ce jeton d’authentification à Primetime Cloud DRM, ainsi que toutes les demandes de licence. Primetime Cloud DRM ne traitera pas ce jeton, mais le transmettra (en tant qu’objet blob opaque) à votre point de terminaison BEES pour traitement.
* **Licence** : demandez une licence pour votre contenu protégé. Le périphérique client ajoute automatiquement votre jeton d’authentification précédemment défini à l’appel.
* **Droits** - Primetime Cloud DRM détermine que le contenu a été compressé avec une stratégie qui requiert BEES. Primetime Cloud DRM construira une requête JSON à envoyer au point de terminaison BEES. La réponse de BEES indique à Primetime Cloud DRM s’il faut ou non délivrer une licence et, éventuellement, quelle stratégie DRM utiliser.

## Détails du processus de stratégie {#policy-workflow-details}

Lorsque Primetime Cloud DRM traite une demande de licence, il analyse la stratégie DRM dans la demande afin de déterminer si un appel à un service de droits d’accès principal est nécessaire avant que le contenu ne s’affiche. Si un appel BEES *est* requis, Primetime Cloud DRM crée la demande BEES, puis analyse la stratégie DRM pour obtenir un point de terminaison d’URL BEES spécifié pour la demande BEES.

Appliquez votre stratégie DRM qui indique l’exigence BEES, en spécifiant les deux propriétés personnalisées suivantes dans la stratégie :

    * `policy.customProp.1=bees.required=&lt;true| false>`
    * `policy.customProp.2=bees.url=&lt;url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Par exemple, à l’aide du Gestionnaire de stratégies DRM Primetime ( [!DNL AdobePolicyManager.jar]), vous spécifiez les deux propriétés personnalisées suivantes dans le fichier de [!DNL flashaccesstools.properties] configuration :

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Si vous utilisez déjà `policy.customProp.1` ou `policy.customProp.2` pour une autre propriété, utilisez simplement des nombres uniques pour les nouvelles propriétés.

## Détails du processus du pack {#package-workflow-details}

Lors de l’assemblage de votre contenu protégé par Adobe Access, vous devez appliquer l’une de vos stratégies DRM prenant en compte les BEES au contenu.

## Détails du processus d’authentification {#authentication-workflow-details}

Pour que votre point de terminaison BEES prenne des décisions de droits, le périphérique client doit fournir des informations d’authentification. Pour ce faire, utilisez votre propre jeton d’authentification spécifique au client.

Primetime Cloud DRM n’a pas besoin de comprendre ce jeton ; il transmet simplement ce jeton à votre point de terminaison BEES. Le périphérique client est chargé de créer ou d’acquérir ce jeton et de le définir à l’aide de l’ `DRMManager.setAuthenticationToken()` API.

Procédez comme suit pour associer ce jeton à Primetime Cloud DRM afin qu’il soit envoyé avec la demande de licence :

Instanciez l’ `DRMManager` objet à l’aide des métadonnées DRM du contenu compressé pour le DRM de Primetime Cloud.

La `setAuthenticationToken()` méthode fonctionne en associant le tableau d’octets donné à l’URL du serveur de licences fournie dans les métadonnées DRM utilisées pour instancier `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Le jeton est envoyé avec toutes les demandes de licence jusqu’à ce que le jeton soit effacé en appelant `.setAuthenticationToken` avec null comme paramètre.

## Détails du processus de licence{#license-workflow-details}

Demandez une licence à Primetime Cloud DRM en appelant `mgr.loadVoucher()`.

## Détails de la demande de droits et de la réponse{#entitlement-request-and-response-details}

Lorsque le DRM de Primetime Cloud détermine que le contenu a été inclus avec une stratégie DRM prenant en charge les BEES, il construit la requête JSON suivante pour l’envoyer au point de terminaison des BEES spécifié dans la stratégie DRM :

```
{
    "title":"Entitlement Request",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"Unique ID for this message. Used to confirm that the
                           returned response is for this particular message."
        },
        "version": {
            "type":"string",
            "description":"BEES Request Version. Currently 1."
        },
        "contentID": {
            "type":"string",
            "description":"Content ID (GUID)"
        },
        "customerSpecificAuthToken": {
            "type":"string",
            "description":"Base64-encoded authentication token. Must be set
                           explicitly by client before making the license request."
        }
    },
    "required": [
        "messageID",
        "version",
        "contentID"
    ]
}
```

La réponse suivante est attendue du point de terminaison BEES :

```
{
    "title":"Entitlement Response",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"ID of the Entitlement Request that this Response is
                           handling. Must exactly match the ID of the request
                           or this response will be rejected."
        },
        "version": {
            "type":"string",
            "description":"BEES Response Version. Currently 1."
        },
        "isAllowed": {
            "type":"boolean",
            "description":"Grant the license or not."
        },
        "policy": {
            "type":"string",
            "description":"Base64-encoded policy to enforce  If no policy is
                           provided, the policy that was packaged with the content
                           during packaging time will be used to generate the license."
        },
        "error": {
            "type":"integer",
            "description":"An error number produced by the entitlement server.
                           Will be passed to the client as the 'code' field of
                           the server error response."
        },
        "errorText": {
            "type":"string",
            "description":"Additional error information produced by the
                           entitlement server. Will be passed to the client as
                           the 'text' field of the server error response."
        }
    },
    "required": [
        "messageID",
        "version",
        "isAllowed"
    ]
}
```

Primetime Cloud DRM utilise la réponse pour déterminer s’il doit ou non délivrer une licence au périphérique demandeur et s’il doit remplacer une nouvelle stratégie DRM dans le processus de génération de la licence. Si `isAllowed` est défini `true` et qu’aucune stratégie n’est fournie dans la réponse, la stratégie DRM d’origine utilisée pendant la période de création du contenu est utilisée pour générer la licence.