---
title: Récupération de la liste des ressources préautorisées par une application web de deuxième écran
description: Récupération de la liste des ressources préautorisées par une application web de deuxième écran
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Récupération de la liste des ressources préautorisées par une application web de deuxième écran {#retrieve-list-of-preauthorized-resources-by-second-screen-web-app}

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

Demande d’authentification Adobe Primetime pour obtenir la liste des ressources préautorisées.

Il existe deux ensembles d’API : un jeu pour l’application de diffusion en continu ou le service de programmation et un autre pour l’application web du deuxième écran. Cette page décrit l’API de l’application AuthN.

 \
| Point de terminaison | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse | | — | — | — | — | — | — | | &lt;sp_fqdn>/api/v1/preautoriser/{code d’enregistrement} | Module AuthN | 1.  code d&#39;enregistrement  </br>    (composant Chemin)</br>2.  demandeur (obligatoire)</br>3.  liste de ressources (obligatoire) | GET | XML ou JSON contenant des décisions de préautorisation individuelles ou des détails d’erreur. Voir les exemples ci-dessous. | 200 - Succès</br></br>400 - Mauvaise requête</br></br>401 - Non autorisé</br></br>405 - Méthode non autorisée  </br></br>412 - Echec de la précondition</br></br>500 - Erreur interne du serveur |



| Paramètre d’entrée | Description |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| code d&#39;enregistrement | La valeur du code d’enregistrement fournie par l’utilisateur au début du flux d’authentification. |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| liste de ressources | Chaîne contenant une liste délimitée par des virgules de resourceIds qui identifie le contenu pouvant être accessible à un utilisateur et reconnu par les points de terminaison d’autorisation MVPD. |


### Exemple de réponse {#sample-response}

**XML :**

```XML
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4`
Adobe-Response-Confidence : full
Content-Type: application/xml; charset=utf-8

<resources>
    <resource>
        <id>TestStream1</id>
        <authorized>true</authorized>
    </resource>
    <resource>
        <id>TestStream2</id>
        <authorized>false</authorized>  
        <error>
            <status>403</status>
            <code>authorization_denied_by_mvpd</code>
            <message>User not authorized</message>
            <details>Your subscription package does not include the "TestStream3" channel.</details>
            <helpUrl>https://tve.helpdocsonline.com/errors/preauthorization_denied</helpUrl>
            <trace>0453f8c8-167a-4429-8784-cd32cfeaee58</trace>
            <action>none</action>
        </error>
    <resource>
</resources>
```

**JSON :**

```JSON
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/json; charset=utf-8
 
{
   "resources" : [
        {
            "id" : "TestStream1",
            "authorized" : true
        },
        {
            "id" : "TestStream3",
            "authorized" : false,
            "error" : {
               "status" : 403,
               "code" : "authorization_denied_by_mvpd",
               "message" : "User not authorized",
               "details" : "Your subscription package does not include the "TestStream3" channel.",
               "helpUrl" : "https://tve.helpdocsonline.com/errors/preauthorization_denied",
               "trace" : "0453f8c8-167a-4429-8784-cd32cfeaee58",
               "action" : "none"
            }
        } 
    ]
}
```
 

### [Retour à la référence de l’API REST](http://tve.helpdocsonline.com/rest-api-reference)
