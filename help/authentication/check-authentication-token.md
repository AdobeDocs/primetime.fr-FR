---
title: Vérifier le jeton d’authentification
description: Vérifier le jeton d’authentification
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Vérifier le jeton d’authentification {#check-authentication-token}

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

Indique si le périphérique dispose d’un jeton d’authentification non expiré.

| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/checkauthn | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur (obligatoire)</br>2.  deviceId (obligatoire)</br>3.  device_info/X-Device-Info (obligatoire)</br>4.  _deviceType_ </br>5.  _deviceUser_ (Obsolète)</br>6.  _appId_ (Obsolète) | GET | XML ou JSON contenant les détails d’erreur en cas d’échec. | 200 - Succès   </br>403 - Pas de succès |

{style=&quot;table-layout:auto&quot;}


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: Il peut s’agir de transférer device_info comme paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, il doit être transmis sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section [Transmission des informations de périphérique et de connexion](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>Si ce paramètre est correctement défini, ESM propose des mesures qui sont [ventilation par type d’appareil](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br>**Remarque**: device_info remplace ce paramètre. |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil. |
| _appId_ | ID/nom de l’application.</br>**Remarque**: device_info remplace ce paramètre. |

{style=&quot;table-layout:auto&quot;}


## Réponse (en cas d’échec) {#response}

```JSON
    <error>
      <status>403</status>
      <message>Authentication token expired</message>
    </error>
```

### [Retour à la référence de l’API REST](http://tve.helpdocsonline.com/rest-api-reference)
