---
title: Référence de l’API REST
description: Référence de l’api REST
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 3%

---


# Référence de l’API REST {#rest-api-reference}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Formats de réponse {#response-formats}


>[!NOTE]
>
> Les API fournies dans ces services peuvent renvoyer des réponses au format XML ou JSON (pour les API qui renvoient une réponse). Il existe 3 manières différentes de spécifier le format de réponse dans la requête :
>* Définissez l’en-tête HTTP Accept sur &quot;application/xml&quot;</code>&quot; ou &quot;application/json</code>&quot;
>* Dans le payload de la requête, spécifiez le paramètre &quot;format=xml&quot;</code>&quot; ou &quot;format=json</code>&quot;</li>
>* Appelez le point d’entrée du service Web avec l’extension .xml .</code> ou .json</code>. Par exemple : &quot;/regcode.xml</code>&quot; ou &quot;/regcode.json</code>&quot;
>
>Vous pouvez spécifier l’une des méthodes ci-dessus. La spécification de plusieurs méthodes avec des formats en conflit peut entraîner des erreurs ou une sortie indésirable.

## Points de terminaison de l’API REST {#clientless-endpoints}

&lt;reggie_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* Production - [api.auth.adobe.com](http://api.auth.adobe.com/)
* Évaluation - [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>


## Résumé des services web {#web_srvs_summary}

Le tableau ci-dessous répertorie les services web disponibles pour l’approche sans client. Cliquez sur les points de terminaison des services web pour plus d’informations (exemple de requête et de réponse, paramètres d’entrée, méthodes HTTP, etc.)


| Sr | Point de terminaison du service Web | Description | [Diag.  </br>Ref](http://tve.helpdocsonline.com/api-reference-v2-test#illustration). | Hébergé à | Appelé par |
| --- | --- | --- | --- | --- | --- |
| 1. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode](http://tve.helpdocsonline.com/registration-code-request) | Renvoie le code d’enregistrement généré de manière aléatoire et l’URI de page de connexion | 2 | Adobe  </br>Service Reg Code | Appareil dynamique |
| 2. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/return-registration-record) | Renvoie l’enregistrement du code d’enregistrement contenant le code d’enregistrement UUID, le code d’enregistrement et l’ID d’appareil haché. | 8 | Adobe  </br>Service Reg Code | Authentification Primetime |
| 3. | [&lt;sp_fqdn>/api/v1/config/  </br>  {requestorId}](http://tve.helpdocsonline.com/provide-mvpd-list) | Renvoie la liste des MVPD configurés pour le demandeur | 5 | Adobe  </br>Primetime  </br>authentication  </br>Service | Connexion  </br>Web  </br>Application |
| 4. | [&lt;sp_fqdn>/api/v1/authenticate](http://tve.helpdocsonline.com/initiate-authentication) | Lance le processus AuthN en informant l’événement de sélection MVPD. Crée un enregistrement sur la base de données d’authentification, qui est réconcilié lorsqu’une réponse réussie est reçue de MVPD (étape 13) | 7 | Adobe  </br>Primetime  </br>authentication  </br>Service | Connexion  </br>Web  </br>Application |
| 5. | Consommateur d’assertion SAML | Processus SAML existant entre l’authentification Primetime et MVPD | 13 | Primetime  </br>authentication  </br>Service | Authentification Primetime |
| 6. | [&lt;sp_fqdn>/api/v1/checkauthn/  </br>  {registrationCode}](http://tve.helpdocsonline.com/check-authentication-flow-by-second-screen-web-app) | L’application Web de connexion peut vérifier si le flux de connexion tenté a réussi. |  | Primetime  </br>authentication   </br>Service | Connexion   </br>Web   </br>Application |
| 7. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | Obtient les métadonnées associées au jeton AuthN | 15 | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 8. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/delete-registration-record) | Supprime l’enregistrement du code reg et le libère pour réutilisation. | 16 | Adobe  </br>Service Reg Code | Authentification Primetime |
| 9. | [&lt;sp_fqdn>/api/v1/authorized](http://tve.helpdocsonline.com/initiate-authorization) | Obtient la réponse d’autorisation. | 17 | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 10. | [&lt;sp_fqdn>/api/v1/checkauthn](http://tve.helpdocsonline.com/check-authentication-token) | Indique si le périphérique dispose d’un jeton AuthN non expiré. |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 11. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | Renvoie le jeton AuthN s’il est trouvé. |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 12. | [&lt;sp_fqdn>/api/v1/tokens/authz](http://tve.helpdocsonline.com/retrieve-authorization-token) | Renvoie le jeton AuthZ s’il est trouvé. |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 13. | [&lt;sp_fqdn>/api/v1/tokens/media](http://tve.helpdocsonline.com/obtain-short-media-token) | Renvoie le jeton de média court s’il est trouvé - identique à /api/v1/mediatoken |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 14. | [&lt;sp_fqdn>/api/v1/mediatoken](http://tve.helpdocsonline.com/obtain-short-media-token) | Obtient un jeton de média court |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 15. | [&lt;sp_fqdn>/api/v1/preauthorized](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources) | Récupère la liste des ressources préautorisées |  | Primetime  </br>authentication  </br>Service | Appareil dynamique |
| 16. | [&lt;sp_fqdn>/api/v1/preautoriser/{code}](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources-by-way-of-web-app) | Récupère la liste des ressources préautorisées |  | Primetime  </br>authentication  </br>Service | Application Web de connexion |
| 17. | [&lt;sp_fqdn>/api/v1/logout](http://tve.helpdocsonline.com/logout) | Supprimer les jetons AuthN et AuthZ du stockage |  | Primetime  </br>authentication   </br>Service | Appareil dynamique |
| 18. | [&lt;sp_fqdn>/api/v1/tokens/usermetadata](http://tve.helpdocsonline.com/user-metadata-call) | Obtient les métadonnées utilisateur une fois le flux d’authentification terminé | N/A | N/A | Appareil dynamique |
| 19. | [&lt;sp_fqdn>/api/v1/authenticate/freepreview](http://tve.helpdocsonline.com/free-preview-for-temp-pass-and-promotional-temp-pass) | Création d’un jeton d’authentification pour Temp Pass ou Promoted Temp Pass | N/A | Primetime  </br>authentication  </br>Service | Appareil dynamique |

{style=&quot;table-layout:auto&quot;}

## Sécurité de l’API REST {#security}

Toutes les API sans client d’authentification Primetime doivent être appelées à l’aide du protocole HTTPS pour une communication sécurisée. En outre, la plupart des API appelées doivent contenir un jeton d’accès fourni par [Enregistrement du client dynamique](http://tve.helpdocsonline.com/dynamic-client-registration).


## Informations connexes {#related}

* [Présentation de l’API REST](http://tve.helpdocsonline.com/reset-api-overview)
* [Guide pas à pas du serveur](http://tve.helpdocsonline.com/server-to-server-cookbook)
* [Guide pas à pas client client-serveur](http://tve.helpdocsonline.com/client-to-server)
* [Évitez d’utiliser &#39;&amp;&#39;reg\_code dans /authenticate request (note technique)](https://tve.zendesk.com/entries/23648011-Clientless-Avoid-using-reg-code-in-authenticate-request)
