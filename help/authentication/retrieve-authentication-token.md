---
title: Récupération du jeton d’authentification
description: Récupération du jeton d’authentification
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Récupération du jeton d’authentification {#retrieve-authentication-token}

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

Récupère le jeton d’authentification (AuthN).  

| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/authn</br></br>Par exemple :</br></br>&lt;sp_fqdn>/api/v1/tokens/authn | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur (obligatoire)</br>2.  deviceId (obligatoire)</br>3.  device_info/X-Device-Info (obligatoire)</br>4.  _deviceType_ (Obsolète)</br>5.  _deviceUser_ (Obsolète)</br>6.  _appId_ (Obsolète) | GET | XML ou JSON contenant des informations d’authentification ou des détails d’erreur en cas d’échec. | 200 - Réussite.  </br>404 - Jeton introuvable  </br>410 - Jeton expiré |

{style=&quot;table-layout:auto&quot;}


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: Cela peut être transmis device_info comme paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, il doit être transmis sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section [Transmission des informations de périphérique et de connexion](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>**Remarque**: device_info remplace ce paramètre. |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil.</br></br>**Remarque**: s’il est utilisé, deviceUser doit avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/registration-code-request) requête. |
| _appId_ | ID/nom de l’application. </br></br>**Remarque**: device_info remplace ce paramètre. Si utilisé, `appId` doivent avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/registration-code-request) requête. |

{style=&quot;table-layout:auto&quot;}

</br>

### Exemple de réponse {#response}

 

#### Succès

**XML :**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authentication>
         <expires>1601114932000</expires>
         <userId>sampleUserId</userId>
         <mvpd>sampleMvpdId</mvpd>
         <requestor>sampleRequestor</requestor>
    </authentication>
```


**JSON :**

```JSON
    {
         "requestor": "sampleRequestor",
         "mvpd": "sampleMvpdId",
         "userId": "sampleUserId",
         "expires": "1601114932000"
    }
```

 

 

#### Jeton d’authentification introuvable :

**XML :**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <error>
        <status>404</status>
        <message>Not found</message>
    </error>
```

 
**JSON :**

```JSON
    {
        "status": 404,
        "message": "Not Found"
    }
```

[Retour à la référence d’API sans client](http://tve.helpdocsonline.com/clientless-api-reference)
