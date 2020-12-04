---
seo-title: Détails du processus de stratégie
title: Détails du processus de stratégie
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---


# Processus BEES {#bees-workflow}

**Résumé :**

* **Stratégie**  - Créez une stratégie de gestion des abeilles (DRM) qui indique que l&#39;abeille est requise pour tout le contenu emballé à l&#39;aide de cette stratégie.
* **Packaging**  - Empaquetage de contenu à l’aide de la stratégie DRM basée sur les ABEES.
* **Authentification**  - Authentifiez votre périphérique client et utilisez l’API DRM Primetime, ou l’API Primetime, pour associer ce jeton à la gestion des droits numériques Primetime Cloud. Ainsi, le périphérique client enverra ce jeton d’authentification à Primetime Cloud DRM avec toutes les demandes de licence. Primetime Cloud DRM ne traitera pas ce jeton, mais le transmettra (en tant que blob opaque) à votre point de terminaison d&#39;abeilles pour traitement.
* **Licence**  - Demandez une licence pour votre contenu protégé. Le périphérique client ajoute automatiquement votre jeton d’authentification précédemment défini à l’appel.
* **Droits**  - Primetime Cloud DRM détermine que le contenu a été inclus avec une stratégie qui requiertBEES. Primetime Cloud DRM construira une demande JSON à envoyer au point de terminaison BEES. La réponse d&#39;BEES indique à Primetime Cloud DRM si une licence doit être émise ou non et, éventuellement, quelle stratégie DRM utiliser.

## Détails du processus de stratégie {#policy-workflow-details}

Lorsque Primetime Cloud DRM traite une demande de licence, il analyse la stratégie DRM dans la demande afin de déterminer si un appel à un service de droits d’arrière-plan est nécessaire avant que le contenu ne s’affiche. Si un appel BEES *est* requis, Primetime Cloud DRM crée la demande BEES, puis analyse la stratégie DRM pour obtenir un point de terminaison d&#39;URL BEES spécifié pour la demande BEES.

Appliquez votre stratégie DRM qui indique l’exigence BEES, en spécifiant les deux propriétés personnalisées suivantes dans la stratégie :

    * `policy.customProp.1=bees.required=&lt;true>`
    * `policy.customProp.2=bees.url=&lt;url to=&quot;&quot; your=&quot;&quot; BEES=&quot;&quot; endpoint=&quot;&quot;>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Par exemple, en utilisant le Gestionnaire de stratégies DRM Primetime ( [!DNL AdobePolicyManager.jar]), vous spécifiez les deux propriétés personnalisées suivantes dans le fichier de configuration [!DNL flashaccesstools.properties] :

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Si vous utilisez déjà `policy.customProp.1` ou `policy.customProp.2` pour une autre propriété, utilisez simplement des numéros uniques pour les propriétés les plus récentes.

## Détails du processus du package {#package-workflow-details}

Lors de la création d&#39;un pack de contenu protégé par accès à l&#39;Adobe, vous devez appliquer l&#39;une de vos stratégies DRM prenant en compte les abeilles au contenu.

## Détails du processus d&#39;authentification {#authentication-workflow-details}

Pour que votre point de terminaison BEES prenne des décisions concernant les droits, le périphérique client doit fournir des informations d’authentification. Pour ce faire, utilisez votre propre jeton d’authentification spécifique au client.

Primetime Cloud DRM n’a pas à comprendre ce jeton ; il le transmet simplement à votre point de terminaison Abeilles. Le périphérique client est chargé de créer ou d’acquérir ce jeton et de le définir à l’aide de l’API `DRMManager.setAuthenticationToken()`.

Pour associer ce jeton à Primetime Cloud DRM, procédez comme suit afin qu’il soit envoyé avec la demande de licence :

Instanciez l’objet `DRMManager` à l’aide des métadonnées DRM du contenu compressé pour Primetime Cloud DRM.

La méthode `setAuthenticationToken()` fonctionne en associant le tableau d’octets donné à l’URL du serveur de licences fournie dans les métadonnées DRM utilisées pour instancier `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Le jeton est envoyé avec toutes les demandes de licence jusqu’à ce que le jeton soit effacé en appelant `.setAuthenticationToken` avec la valeur null comme paramètre.

## Détails du processus de licence{#license-workflow-details}

Demandez une licence à Primetime Cloud DRM en appelant `mgr.loadVoucher()`.

## Détails de la demande et de la réponse de droits{#entitlement-request-and-response-details}

Lorsque le DRM de Primetime Cloud détermine que le contenu a été inclus avec une stratégie DRM prenant en compte les abeilles, il construit la demande JSON suivante pour envoyer au point de terminaison des abeilles spécifié dans la stratégie DRM :

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

La réponse suivante est attendue à partir du point de terminaison des abeilles :

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

Primetime Cloud DRM utilise la réponse pour déterminer s’il doit ou non délivrer une licence au périphérique demandeur et s’il doit remplacer une nouvelle stratégie DRM dans le processus de génération de licence. Si `isAllowed` est `true` et qu&#39;aucune stratégie n&#39;est fournie dans la réponse, la stratégie DRM d&#39;origine utilisée pendant la durée de création du contenu est utilisée pour générer la licence.