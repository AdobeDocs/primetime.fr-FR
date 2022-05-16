---
title: Détails du workflow de stratégie
description: Détails du workflow de stratégie
copied-description: true
exl-id: e3daf7a9-def0-48a9-8190-adb25eec7b59
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Processus BEES {#bees-workflow}

**Résumé :**

* **Stratégie** - Créez une stratégie DRM BEES qui indique que BEES est nécessaire pour tout le contenu empaqueté à l’aide de cette stratégie.
* **Modules** - Regroupez le contenu à l’aide de la stratégie DRM basée sur les BEES.
* **Authentification** - Authentifiez votre appareil client et utilisez l’API Primetime DRM, ou l’API Primetime, pour associer ce jeton à Primetime Cloud DRM. Ce faisant, l’appareil client enverra ce jeton d’authentification à Primetime Cloud DRM avec toutes les demandes de licence. Primetime Cloud DRM ne traitera pas ce jeton, mais le transmettra (en tant qu’objet blob opaque) à votre point de terminaison BEES pour le traitement.
* **Licences** - Demandez une licence pour votre contenu protégé. Le périphérique client ajoute automatiquement votre jeton d’authentification défini précédemment à l’appel .
* **Droit** - Primetime Cloud DRM détermine que le contenu a été compilé avec une stratégie qui nécessite BEES. Primetime Cloud DRM crée une requête JSON à envoyer au point de terminaison BEES. La réponse BEES indiquera à Primetime Cloud DRM d’émettre ou non une licence et, éventuellement, la stratégie DRM à utiliser.

## Détails du workflow de stratégie {#policy-workflow-details}

Lorsque Primetime Cloud DRM traite une demande de licence, il analyse la stratégie DRM dans la demande pour déterminer si un appel à un service de droit principal est requis avant que le contenu puisse être affiché. Si un appel BEES *is* Si nécessaire, Primetime Cloud DRM crée la requête BEES, puis analyse la stratégie DRM pour obtenir un point de terminaison d’URL BEES spécifié pour la requête BEES.

Appliquez votre stratégie DRM qui indique l’exigence BEES, en spécifiant les deux propriétés personnalisées suivantes dans la stratégie :

* `policy.customProp.1=bees.required=<true | false>`
* `policy.customProp.2=bees.url=<url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

Par exemple, en utilisant Primetime DRM Policy Manager ( [!DNL AdobePolicyManager.jar]), vous devez spécifier les deux propriétés personnalisées suivantes dans la variable [!DNL flashaccesstools.properties] fichier de configuration :

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>Si vous utilisez déjà `policy.customProp.1` ou `policy.customProp.2` pour une autre propriété, utilisez simplement des numéros uniques pour les propriétés les plus récentes.

## Détails du workflow de module {#package-workflow-details}

Lors du conditionnement du contenu protégé par accès de votre Adobe, vous devez appliquer l’une de vos stratégies DRM basées sur les abeilles au contenu.

## Détails du workflow d’authentification {#authentication-workflow-details}

Pour que votre point de terminaison BEES puisse prendre des décisions concernant les droits, l’appareil client doit fournir des informations d’authentification. Pour ce faire, utilisez votre propre jeton d’authentification spécifique au client.

Primetime Cloud DRM n’a pas à comprendre ce jeton ; il le transmet simplement à votre point de terminaison BEES. L’appareil client est chargé de créer ou d’acquérir ce jeton et de le définir à l’aide de la fonction `DRMManager.setAuthenticationToken()` API.

Procédez comme suit pour associer ce jeton à Primetime Cloud DRM , de sorte qu’il soit envoyé avec la demande de licence :

Instanciation de la variable `DRMManager` avec les métadonnées DRM du contenu qui a été mis en package pour Primetime Cloud DRM.

Le `setAuthenticationToken()` fonctionne en associant le tableau d’octets donné à l’URL du serveur de licences fournie dans les métadonnées DRM utilisées pour instancier. `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

Le jeton est envoyé avec toutes les demandes de licence jusqu’à ce que le jeton soit effacé en appelant `.setAuthenticationToken` avec la valeur null comme paramètre.

## Détails du workflow de licence{#license-workflow-details}

Demandez une licence à Primetime Cloud DRM en appelant `mgr.loadVoucher()`.

## Détails de la requête et de la réponse de droit{#entitlement-request-and-response-details}

Lorsque Primetime Cloud DRM détermine que le contenu a été compilé avec une stratégie DRM prenant en charge l’BEES, il crée la requête JSON suivante à envoyer au point de terminaison BEES spécifié dans la stratégie DRM :

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

Primetime Cloud DRM utilise la réponse pour déterminer s’il doit ou non émettre une licence sur l’appareil demandeur et s’il doit substituer une nouvelle stratégie DRM dans le processus de génération de licence. If `isAllowed` is `true` et qu’aucune stratégie n’est fournie dans la réponse, la stratégie DRM d’origine utilisée pendant le délai de création du contenu sera utilisée pour générer la licence.
