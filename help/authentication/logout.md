---
title: Lancer la déconnexion
description: Lancement de la déconnexion
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Lancer la déconnexion {#initiate-logout}

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

Supprimez les jetons AuthN et AuthZ du stockage.


| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/logout | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur</br>2.  deviceId (obligatoire)</br>3.  device_info/X-Device-Info (obligatoire)</br>4.  _deviceType_</br> 5.  _deviceUser_ (Obsolète)</br>6.  _appId_ (Obsolète) | DELETE | Aucun | 204 |


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: Cela peut être transmis device_info comme paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, il doit être transmis sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section [Transmission des informations de périphérique et de connexion](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>Si ce paramètre est correctement défini, ESM propose des mesures qui sont [ventilation par type d’appareil](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Remarque**: device_info remplace ce paramètre. |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil.</br></br>**Remarque**: s’il est utilisé, deviceUser doit avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/registration-code-request) requête. |
| _appId_ | ID/nom de l’application. </br></br>**Remarque**: device_info remplace ce paramètre. Si utilisé, `appId` doivent avoir les mêmes valeurs que dans la variable [Créer un code d’enregistrement](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) requête. |

>[!IMPORTANT]
> 
>L’appel de déconnexion présente actuellement les limites suivantes : il efface les jetons AuthN et AuthZ du stockage (c’est-à-dire du côté de l’authentification Programmer/Primetime), mais **ne fait pas** appelez le point de terminaison de déconnexion MVPD . 

### [Retour à la référence de l’API REST](/help/authentication/rest-api-reference.md)
