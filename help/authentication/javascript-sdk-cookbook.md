---
title: Guide pas à pas du SDK JavaScript
description: Guide pas à pas du SDK JavaScript
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---


# Guide pas à pas du SDK JavaScript {#javascript-sdk-cookbook}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Introduction (#intro)

Ce document décrit les processus de droits que l’application de niveau supérieur d’un programmeur implémente pour une intégration JavaScript avec le service d’authentification Adobe Primetime. Les liens vers la référence API JavaScript sont inclus dans tout le contenu.

Notez également que la variable [Informations connexes](#related) comprend un lien vers un ensemble d’exemples de code JavaScript.

## Flux de droits (#entitlement)

1. [Conditions préalables](#prereq)
2. [Flux de démarrage](#startup)
3. [Flux d’authentification](#authn)
4. [Flux d’autorisation](#authz)
5. [Afficher le flux du média](#logout)

</br>

![](assets/javascript-flows.png)


## Conditions préalables(#prereq)

**Dépendances :**

- Bibliothèque d’authentification Adobe Primetime (AccessEnabler), adressez-vous à votre gestionnaire de compte d’authentification Adobe Primetime pour le faire.
- Identifiant de demandeur d’authentification Adobe Primetime valide, contactez votre gestionnaire de compte d’authentification Adobe Primetime pour arranger cela.

Créez vos fonctions de rappel :

- `entitlementLoaded`

</br>

**Déclencheur :** L’initialisation d’AccessEnabler est terminée et chargée.

- `displayProviderDialog(mvpds)`

   **Déclencheur :** `getAuthentication(),` uniquement si l’utilisateur n’a pas sélectionné de fournisseur (MVPD) et n’est pas encore authentifié. Le paramètre mvpds est un tableau de fournisseurs disponibles pour l’utilisateur.

- `setAuthenticationStatus(status, errorcode)`

   **Déclencheur :**
   - `checkAuthentication()`à chaque fois.
   - `getAuthentication()` uniquement si l’utilisateur est déjà authentifié et a sélectionné un fournisseur.

   L’état renvoyé est un succès ou un échec. le code d’erreur décrit le type de l’échec.

- `createIFrame(width, height)`

   **Déclencheur :** `setSelectedProvider(providerID)`, uniquement si le fournisseur sélectionné est configuré pour s’afficher dans un IFrame.

   >[!NOTE]
   >
   >Un fournisseur est configuré pour afficher son écran d’authentification sous la forme d’une redirection ou dans un iFrame, et le programmeur doit tenir compte des deux.

- `sendTrackingData(event, data)`

   **Triggers :** `checkAuthentication(), getAuthentication(),checkAuthorization(), getAuthorization(), setSelectedProvider()`.  Le `event` indique l’événement de droit qui s’est produit ; la valeur `data` est une liste de valeurs relatives à l’événement. 
- `setToken(token, resource)`

   **Déclencheur :** `checkAuthorization()`et `getAuthorization()` après une autorisation d’affichage d’une ressource.   Le `token` est le jeton multimédia de courte durée ; la valeur `resource` est le contenu que l’utilisateur est autorisé à afficher.

- `tokenRequestFailed(resource, code, description)`

   **Déclencheur :**`checkAuthorization()` et`getAuthorization()`  après une autorisation manquée.\
   Le `resource` est le contenu que l’utilisateur tentait d’afficher ; la valeur `code` est le code d’erreur indiquant le type d’échec ; la valeur `description` décrit l’erreur associée au code d’erreur.

- `selectedProvider(mvpd)`

   **Déclencheur :** [`getSelectedProvider()`](#$getSelProv Le `mvpd` fournit des informations sur le fournisseur sélectionné par l’utilisateur.

- `setMetadataStatus(metadata, key, arguments)`

   **Déclencheur :** `getMetadata().`\
   Le `metadata` fournit les données spécifiques demandées ; le paramètre key est la clé utilisée dans la variable `getMetadata()`demande; et le `arguments` est le même dictionnaire que celui qui a été transmis à `getMetadata()`.


## 2. Flux de démarrage

**I. Chargez le JavaScript AccessEnabler :**

**Pour le profil d’évaluation**

```JSON
<script type="text/javascript"         
src="https://entitlement.auth-staging.adobe.com/entitlement/v4/AccessEnabler.js">
</script>"
```

ou ...

**Pour le profil de production**

```JSON
<script type="text/javascript"         
src="https://entitlement.auth.adobe.com/entitlement/v4/AccessEnabler.js">
</script>"
```

**Triggers :** Une fois l’initialisation terminée, l’authentification Adobe Primetime appelle votre `entitlementLoaded()` fonction de rappel. Il s’agit du point d’entrée de la communication de votre application avec AccessEnabler. 

 
**II.** Appeler `setRequestor()`établir l&#39;identité du programmeur; transmettez le `requestorID` et (éventuellement) un tableau de points de terminaison d’authentification Adobe Primetime.

**Triggers :** Aucun, mais active `displayProviderDialog()` à appeler si nécessaire.


**III.** Appeler `checkAuthentication()` pour rechercher une authentification existante sans initialiser l’ensemble [flux d’authentification].  Si cet appel réussit, vous pouvez passer directement à la variable `authorization flow`.  Si ce n’est pas le cas, passez à la `authentication flow`.

**Dépendance :** Un appel réussi à `setRequestor()`(cette dépendance s’applique également à tous les appels suivants).

 **Triggers :** `setAuthenticationStatus()` callback

</br>

## 3. Flux d’authentification</span>


**Dépendance :** Un appel réussi à `setRequestor()`(cette dépendance s’applique également à tous les appels suivants).


Appeler `getAuthentication()` pour obtenir l’état d’authentification OU pour déclencher le flux d’authentification du fournisseur.

**Déclencheurs :**

- `displayProviderDialog()`si l’utilisateur n’a pas encore été authentifié ;
- `setAuthenticationStatus()` si l’authentification a déjà eu lieu

La fin du flux d’authentification est atteinte lors des appels AccessEnabler `setAuthenticationStatus()`avec `isAuthenticated == 1`.

## 4. Flux d’autorisation (#authz)

**Dépendances :**

- Un appel réussi à `setRequestor()` (cette dépendance s’applique également à tous les appels suivants).
- ID de ressource valide accepté par le ou les MVPD. Notez que les ResourceID doivent être identiques à ceux utilisés sur d’autres appareils ou plateformes et seront identiques sur plusieurs MVPD.

Appeler `getAuthorization()` et transmettez le ResourceID pour le média demandé. Un appel réussi renvoie un jeton de média court, qui confirme que l’utilisateur est autorisé à afficher le média demandé.

- Si l’appel est transmis : L’utilisateur dispose d’un jeton AuthN valide et est autorisé à regarder le média demandé.
- Si l’appel échoue : Examinez l’exception générée pour déterminer son type (AuthN, AuthZ ou autre) :
- Si l’appel était une erreur AuthN, redémarrez le flux AuthN.
- Si l’appel était une erreur AuthZ, l’utilisateur n’est pas autorisé à regarder le média demandé et un message d’erreur de ce type doit s’afficher à l’utilisateur.
- En cas d’erreur (erreur de connexion, erreur réseau, etc.) puis afficher un message d’erreur approprié à l’utilisateur.

Utilisez le vérificateur de jeton multimédia pour valider le shortMediaToken renvoyé par un `getAuthorization()` appelez .

 
**Dépendance :** Vérification du jeton de média court (inclus dans la bibliothèque AccessEnabler)

- Si la validation réussit : Affichez/lisez le média demandé pour l’utilisateur.
- En cas d’échec : Le jeton AuthZ n’était pas valide, la demande de média doit être refusée et un message d’erreur doit s’afficher à l’utilisateur.

## 5. Afficher le flux multimédia (#logout)

- L’utilisateur sélectionne le média à afficher.
   - Les médias sont-ils protégés ?\
          - Votre application vérifie si le média est protégé :
      - Si le média est protégé, votre application lance le flux d’autorisation (AuthZ) ci-dessus.
      - Si le média n’est pas protégé, passez à l’affichage du flux multimédia.
      - Média de lecture

## Configuration de l’identifiant visiteur (#visitorID)

Configuration d’un [visitorID Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcvid/) est très important du point de vue d’analytics. Une fois la valeur visitorID d’un EC définie, le SDK envoie ces informations avec chaque appel réseau et le service d’authentification Adobe Primetime collecte ces informations. De cette manière, vous pourrez mettre en corrélation les données d’analyse du service d’authentification Adobe Primetime avec tout autre rapport d’analyse que vous pourriez avoir d’autres applications ou sites web. Vous trouverez des informations sur la configuration de l’identifiant visiteur EC. [here](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=en).

 
>[!NOTE]
>
>Notez que cette prise en charge de cette fonctionnalité est disponible à partir de la version 3.1.0 du SDK JS. 

<!--
### Related Information (#related)

* [JavaScript SDK Overview](/help/authentication/javascript-sdk-overview.md)
* [JavaScript SDK API Reference](/help/authentication/javascript-sdk-api-reference.md)
* **JavaScript SDK Code Samples**
-->