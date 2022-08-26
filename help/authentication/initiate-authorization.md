---
title: Lancer l’autorisation
description: Lancer l’autorisation
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Lancer l’autorisation {#initiate-authorization}

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

Obtient la réponse d’autorisation. 

| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/authorized | Application de diffusion en continu</br></br>ou</br></br>Service de programmation | 1. demandeur (obligatoire)</br>2.  deviceId (obligatoire)</br>3.  resource (obligatoire)</br>4.  device_info/X-Device-Info (obligatoire)</br>5.  _deviceType_</br> 6.  _deviceUser_ (Obsolète)</br>7.  _appId_ (Obsolète)</br>8.  Paramètres supplémentaires (facultatif) | GET | XML ou JSON contenant les détails de l’autorisation ou les détails de l’erreur en cas d’échec. Voir les exemples ci-dessous. | 200 - Succès  </br>403 - Pas de succès |

{style=&quot;table-layout:auto&quot;}

</br>


| Paramètre d’entrée | Description |
| --- | --- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| deviceId | Octets d’identifiant de l’appareil. |
| resource | Chaîne contenant un resourceId (ou fragment MRSS), identifiant le contenu demandé par un utilisateur et reconnu par les points de terminaison d’autorisation MVPD. |
| device_info/</br></br>X-Device-Info | Informations sur les périphériques de diffusion en continu.</br></br>**Remarque**: Cela peut être transmis device_info comme paramètre d’URL, mais en raison de la taille potentielle de ce paramètre et des limitations de longueur d’une URL de GET, il doit être transmis sous la forme X-Device-Info dans l’en-tête http. </br></br>Consultez les détails complets de la section [Transmission des informations de périphérique et de connexion](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | Type d’appareil (par exemple, Roku, PC).</br></br>Si ce paramètre est correctement défini, ESM propose des mesures qui sont [ventilation par type d’appareil](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**Remarque**: device_info remplace ce paramètre. |
| _deviceUser_ | Identifiant de l’utilisateur de l’appareil. |
| _appId_ | ID/nom de l’application. </br></br>**Remarque**: device_info remplace ce paramètre. |
| paramètres supplémentaires | L&#39;appel peut également contenir des paramètres facultatifs qui permettent d&#39;accéder à d&#39;autres fonctionnalités telles que :</br></br>* generic_data - permet l’utilisation de [TempPass Promotionnel](https://tve.helpdocsonline.com/promotional-temp-pass)</br></br>Exemple : `generic_data=("email":"email@domain.com")` |

{style=&quot;table-layout:auto&quot;}

>[!CAUTION]
>
>**Adresse IP du périphérique de diffusion**</br>
>Pour les mises en oeuvre client-serveur, l’adresse IP du périphérique en flux continu est implicitement envoyée avec cet appel.  Pour les implémentations serveur à serveur, où la variable **regcode** L’appel est effectué par le service de programmation et non par le périphérique de diffusion en continu, l’en-tête suivant est nécessaire pour transmettre l’adresse IP du périphérique de diffusion en continu :</br></br>
>
>
```
>X-Forwarded-For : <streaming\_device\_ip>
>```
>
>where `<streaming\_device\_ip>` est l’adresse IP publique du périphérique de diffusion en continu.</br></br>
>Exemple :</br>
>
>
```
>POST /reggie/v1/{req_id}/regcode HTTP/1.1
>X-Forwarded-For:203.45.101.20
>```


### Exemple de réponse {#sample-response}

* **Cas 1 : Succès**

</br>
  * **XML:**
  </br>
    "XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <authorization>
    <expires>1348148289000</expires>
    <mvpd>sampleMvpdId</mvpd>
    <requestor>sampleRequestorId</requestor>
    <resource>sampleResourceId</resource>
    </authorization>
    "



* **JSON :**

   ```JSON
   {
     "mvpd": "sampleMvpdId",
     "resource": "sampleResourceId",
     "requestor": "sampleRequestorId",
     "expires": "1348148289000"
   }
   ```

>[!IMPORTANT]
>
>Lorsque la réponse provient d’un MVPD de proxy, il peut inclure un élément supplémentaire nommé `proxyMvpd`. 

 

* **Cas 2 : Autorisation refusée**


   ```JSON
   <error>
     <status>403</status>
     <message>User not authorized</message>
     <details>Your subscription package does not include the "ASFAFD" channel.
     Please go to http://www.ca.ble/upgrade in order to upgrade your subscription.</details>
   </error>
   ```

[Retour à la référence de l’API REST](http://tve.helpdocsonline.com/rest-api-reference)
