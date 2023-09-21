---
title: Fournir la liste MVPD
description: Fournir la liste MVPD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Fournir la liste MVPD {#provide-mvpd-list}

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

Renvoie la liste des MVPD configurés pour le demandeur.

| Point d’entrée | Appelé  </br>Par | Entrée   </br>Paramètres | HTTP  </br>Méthode | Réponse | HTTP  </br>Réponse |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/config/{requestorId}</br></br>Par exemple :</br></br>&lt;sp_fqdn>/api/v1/config/sampleRequestorId | Authentification Primetime | 1. Demandeur</br>    (composant Chemin)</br>_2.  deviceType (désapprouvé)_ | GET | XML ou JSON contenant la liste des MVPD. | 200 |

{style="table-layout:auto"}


| Paramètre d’entrée | Description |
| --------------- | ------------------------------------------------------------- |
| demandeur | Identifiant du demandeur du programmeur pour lequel cette opération est valide. |
| *deviceType* | Type de périphérique. |

{style="table-layout:auto"}

### Exemple de réponse {#sample-response}

Identique à la réponse XML MVPD existante au servlet /config

Remarque : tous les MVPD configurés pour utiliser la fonction SSO de Platform auront les propriétés supplémentaires suivantes dans leur noeud correspondant (JSON/XML) :

* **enablePlatformServices (booléen) :** Indicateur précisant si ce MVPD est intégré via l’authentification unique de Platform
* **boardingStatus (string):** Indicateur précisant si le MVPD prend entièrement en charge la fonction SSO de Platform (SUPPORTED) ou si le MVPD apparaît uniquement dans le sélecteur de plateforme (PICKER).
* **displayInPlatformPicker (booléen) :** ce MVPD doit-il apparaître dans le sélecteur de plateforme ?
* **platformMappingId (string):** l’identifiant de ce MVPD connu par la plateforme
* **requiredMetadataFields (tableau de chaîne) :** les champs de métadonnées utilisateur censés être disponibles lors d’une connexion réussie ;
