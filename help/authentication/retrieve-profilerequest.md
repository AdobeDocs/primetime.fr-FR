---
title: Récupération de la requête de profil SSO Platform
description: Récupération de la requête de profil SSO Platform
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Récupération de la requête de profil SSO Platform {#retrieve-platform-sso-profile-request}

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

Cette ressource génère des requêtes de profil pour un ID de demandeur et un tuple MVPD.


| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/{requestor}/profile-requests/{mvpd} | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur (paramètre de chemin d’accès)</br>2. mvpd (paramètre de chemin)</br>3. deviceType (obligatoire) | GET | La réponse Content-Type est application/octet-stream, car la charge utile réelle est opaque pour l’application cliente.</br></br>La réponse doit être transmise à Platform par l’application.</br></br>Moteur d’authentification unique pour obtenir une authentification unique du profil. | 200 - Succès   </br>400 - Mauvaise requête |


| Paramètre d’entrée | Description |
| --------------- | -------------------------------------------------------------------------------------------------------- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| mvpd | Identifiant MVPD pour lequel cette opération est valide. |
| deviceType | Plateforme Apple pour laquelle nous tentons d’obtenir une requête de profil.  Soit **iOS** ou **tvOS**. |
