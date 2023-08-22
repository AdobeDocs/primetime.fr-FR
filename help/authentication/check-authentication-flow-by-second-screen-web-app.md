---
title: Vérification du flux d’authentification par application web de deuxième écran
description: Vérification du flux d’authentification par application web de deuxième écran
exl-id: 5807f372-a520-4069-b837-67ae41b7f79b
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Vérification du flux d’authentification par application web de deuxième écran {#check-authentication-flow-by-second-screen-web-app}

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

Cette API doit être utilisée par la seconde application web de connexion à l’écran pour confirmer que l’authentification Adobe Primetime a confirmé la connexion réussie de MVPD. Nous vous recommandons d’appeler cette API avant d’afficher un message de réussite à l’utilisateur final qui lui indique de passer à la console de l’appareil pour continuer les workflows.


| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| SP_FQDN/api/v1/checkauthn/{code d’enregistrement} | Application Web de connexion | 1. code d’enregistrement  </br>    (composant Chemin)</br>2.  demandeur  </br>    (obligatoire) | GET | XML ou JSON contenant les détails d’erreur en cas d’échec. | 200 - Succès   </br>403 - Interdit |

</br>

| Paramètre d’entrée | Description |
| ----------------- | --------------------------------------------------------------------------------------------- |
| code d&#39;enregistrement | La valeur du code d’enregistrement fournie par l’utilisateur au début du flux d’authentification. |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |


### Exemple de réponse (en cas d’erreur) {#response}

```JSON
    {
        "status": 403,
        "message": "Forbidden"
    }
```

### [Retour à la référence de l’API REST](/help/authentication/rest-api-reference.md)
