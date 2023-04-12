---
title: Enregistrement du client dynamique
description: Enregistrement du client dynamique
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Enregistrement du client dynamique {#dynamic-client-registration}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Contexte {#context}

Pour s’aligner sur les pratiques de sécurité modernes, améliorer les exigences des propriétaires d’expérience utilisateur et de plateformes, le SDK Android pour l’authentification Adobe Primetime et le SDK iOS vont dans le sens de l’adoption [Onglets personnalisés Android Chrome](https://developer.chrome.com/multidevice/android/customtabs){target=_blank} and [Apple Safari view controller](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller){target=_blank}.

La mise en oeuvre actuelle d’AdobePass utilise des vues web spécifiques à la plateforme afin de fournir un environnement web pour l’affichage de la page de connexion MVPD. Ces vues web ne partagent pas la gestion des informations d’identification avec les navigateurs de plateforme. Par conséquent, l’utilisateur ne peut pas utiliser de mot de passe enregistré dans un navigateur lors de l’utilisation d’une application d’authentification Adobe Primetime. De plus, pour des raisons de sécurité, certaines plateformes sont en train de rendre obsolètes les contrôleurs WebView pour les tâches d’authentification. Google et Apple offrent des options alternatives telles que &quot;Chrome Custom Onglets&quot; et &quot;Safari View Controller&quot;. Il s’agit essentiellement d’onglets à usage unique de leurs navigateurs respectifs. L’authentification Adobe Primetime adoptera ces nouveaux composants en 2018.

## Détails {#details}

Actuellement, l’authentification Adobe Pass peut identifier et enregistrer les applications de deux manières différentes :

* les clients basés sur un navigateur sont enregistrés par le biais de listes de domaines autorisées.
* les clients d’application natifs, tels que les applications iOS et Android, sont enregistrés par le biais du mécanisme de requête signé.

Afin de répondre aux nouveaux flux pour Chrome Custom Tabs et Safari View Controller, Adobe Pass propose un nouveau mécanisme d’enregistrement des clients pour les nouvelles applications. Ce mécanisme permettra un contrôle plus sécurisé et plus précis de vos applications et peut être utilisé pour enregistrer des applications sur toutes les plateformes.

<!--
## Related Information

- [Dynamic Client Registration API](/help/authentication/dynamic-client-registration-api.md)
- [Dynamic Client Registration Management](/help/authentication/dynamic-client-registration-management.md)
-->