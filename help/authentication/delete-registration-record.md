---
title: Supprimer un enregistrement d’enregistrement
description: Supprimer le enregistrement
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Supprimer un enregistrement d’enregistrement {#delete-registration-record}

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


## Description {#delete-record}

Supprime l’enregistrement du code reg et le libère pour réutilisation. 

| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;reggie_fqdn>/reggie/v1/{requestorId}/regcode/{registrationCode}</br></br>Par exemple :</br></br>&lt;reggie_fqdn>/reggie/v1/regcode/ER45RTY | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. Identifiant du demandeur  </br>    (composant Chemin)</br>2.  Code d’enregistrement  </br>    (composant Chemin) | DELETE | Aucun | 204 |

{style=&quot;table-layout:auto&quot;}

</br>

| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| code d&#39;enregistrement | La valeur du code d’enregistrement qui s’afficherait sur le périphérique de diffusion (à saisir dans le flux d’authentification). |

{style=&quot;table-layout:auto&quot;}

</br>

### [Retour à la référence de l’API REST](http://tve.helpdocsonline.com/rest-api-reference)
