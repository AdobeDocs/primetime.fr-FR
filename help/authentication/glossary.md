---
title: Glossaire
description: Glossaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Glossaire {#glossary}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## AccessEnabler {#accessEnabler}

Composant client de l’authentification Adobe Primetime. L’authentification Adobe Primetime fournit une bibliothèque AccessEnabler pour chaque plateforme prise en charge.

## AuthN {#authn}

Utilisé comme raccourci pour &quot;authentification&quot;, comme dans &quot;Jeton AuthN&quot; ou &quot;Flux AuthN&quot;.


## Jeton AuthN{#authn-token}

Jeton d’authentification, généré par l’authentification Adobe Primetime après l’authentification d’un utilisateur avec un MVPD. Selon la plateforme d’intégration du programmeur, le jeton est stocké sur l’appareil de l’utilisateur ou sur les serveurs d’authentification Adobe Primetime.

## AuthZ {#authz}

Utilisé comme raccourci pour &quot;autorisation&quot;, comme dans &quot;Jeton AuthZ&quot; ou &quot;Flux AuthZ&quot;.

## Jeton AuthZ {#authz-token}

Jeton d’autorisation, généré par l’authentification Adobe Primetime après qu’un utilisateur a été autorisé à afficher du contenu protégé. Le jeton AuthZ est stocké sur les serveurs d’authentification Adobe Primetime et est utilisé pour générer un [Jeton de média de courte durée](#short-lived-token).

## Identifiant de canal (obsolète) {#channel_id}

Ancien terme pour l’ID de ressource.

## API sans client {#clientless-api}

Une solution d’intégration d’authentification Adobe Primetime qui utilise des services web au lieu du composant client AccessEnabler.

## ID de périphérique {#device-id}

Identifie de manière unique un appareil (téléphone, tablette, etc.) dans l’authentification Adobe Primetime. Cet identifiant est obtenu/fourni par l’application du programmeur.


## Flux de droits{#entitlement_flow}

Terme utilisé dans la documentation d’authentification Adobe Primetime pour désigner l’ensemble du processus d’enregistrement d’un appareil/utilisateur avec l’authentification Adobe Primetime, l’authentification d’un utilisateur avec un MVPD, l’autorisation d’une ressource pour un utilisateur et la déconnexion d’un utilisateur.


## GUID {#guid}

Voir [Identifiant utilisateur](#user-id).

## IdP {#idp}

Identifiez le fournisseur ; synonyme de MVPD dans le contexte du rôle d’un MVPD dans une intégration d’authentification Adobe Primetime. (Les clients doivent vérifier leur identité via la page de connexion de leur fournisseur de télévision payante.)

## Vérificateur de jeton multimédia {#media-token-verifier}

Bibliothèque fournie par l’Adobe et utilisée par les programmeurs pour vérifier le jeton multimédia de courte durée généré par l’authentification Adobe Primetime après la réussite d’un flux de droits.

## MVPD {#mvpd}

Distributeur de programmation vidéo multicanal ; synonyme de &quot;fournisseur de télévision payante&quot;.

## MVPD ID {#mvpd-id}

Voir [Identifiant utilisateur](#user-id).

## Identifiant du partenaire {#partner-id}

Identifiant que l’Adobe transmet aux MVPD, qui l’utilise pour identifier au nom duquel l’authentification Adobe Primetime demande l’authentification. Parfois est-il utilisé pour configurer leurs interfaces utilisateur pour des programmeurs particuliers, parfois c&#39;est le même pour tous les programmeurs, ça dépend des besoins du MVPD.

## Prestataire de télévision payante {#pay-tv-provider}

Synonyme de [MVPD](#mvpd).

## Programmeur {#programmer}

Synonyme de &quot;fournisseur de contenu&quot;, &quot;compte&quot;, &quot;canal&quot;, &quot;fournisseur de services&quot;, &quot;marque&quot;, etc.

## Proxy MVPD {#proxy-mvpd}

Un MVPD qui fournit des services d’identité pour d’autres MVPD ; directement intégré à l’authentification Adobe Primetime.

## MVPD proxy {#proxied-mvpd}

Un MVPD qui ne dispose pas d’une intégration directe avec le SP d’Adobe, mais qui est intégré via un MVPD de proxy.

## Identifiant du demandeur {#requestor-id}

Identifie de manière unique un [Programmeur](#programmer) (un compte, une marque, un canal ou une propriété) dans l’authentification Adobe Primetime. Cet identifiant est déterminé entre le programmeur et l’Adobe lors de la configuration initiale du compte. Sur le web, l’identifiant du demandeur est associé à un ensemble de domaines placés sur liste blanche ; tout appel utilisant un identifiant provenant d’un domaine externe sera refusé. Les programmeurs utilisent également l’identifiant du demandeur pour les analyses. Il n’y a généralement qu’un seul identifiant de demandeur par programmeur. Une autre fonctionnalité liée à l’identifiant du demandeur est que le programmeur doit fournir à l’Adobe un certificat public, car l’appel de l’API setRequestor attend l’envoi de données chiffrées, utilisées pour authentifier le programmeur dans le système d’authentification Adobe Primetime.

## ID de ressource {#resource-id}

Chaîne ou ressource mRSS qui identifie une [Programmeur](#programmer) aux MVPD. Il est convenu entre le programmeur et les MVPD ; l’authentification Adobe Primetime transmet l’ID de ressource sans modification, de sorte qu’il doit être le même pour tous les MVPD. Un programmeur peut utiliser plusieurs ID de ressource tant que les MVPD savent ce que chaque ID représente.

## SessionGUID {#sessionGUID}

Voir [Identifiant utilisateur](#user-id).

## Jeton de média de courte durée {#short-lived-token}

Ce jeton est généré par l’authentification Adobe Primetime une fois le processus de droits terminé avec succès pour un utilisateur particulier. Le jeton est transmis au programmeur, qui utilise le vérificateur de jeton d’authentification Adobe Primetime sur le jeton de média de courte durée pour vérifier la sécurité du processus de droit.

## Appareil dynamique {#smart-device}

Terme utilisé dans la documentation d’authentification d’Adobe Primetime pour désigner les décodeurs, les consoles de jeux et les téléviseurs intelligents. Il s’agit de périphériques dotés de fonctionnalités de mise en réseau, mais qui ne sont pas capables de générer des pages web.

## SP{#sp}

Fournisseur de services ; il s’agit généralement de la variable *rôle* de SP, joué par l’authentification Adobe Primetime, agissant pour le compte d’un programmeur dans une intégration avec une [MVPD](#mvpd).

## Temp Pass {#temp-pass}

Fonctionnalité qui permet aux programmeurs de fournir un accès gratuit temporaire au contenu payant. L’accès est par demandeur, pour une période spécifiée par le programmeur.

## TTL {#ttl}

Le Temps De Vivre. Il s’agit de la durée de validité spécifiée d’un jeton.

## TVE {#tve}

La Télévision Partout.

## Identifiant utilisateur {#user-id}

Identifie de manière unique l’utilisateur de l’application d’un programmeur, mais provient du MVPD. Disponible dans différents formulaires pour différents cas pratiques. Voir [Présentation des identifiants utilisateur dans le programme](/help/authentication/programmer-overview.md#user-ids).

## Liste autorisée {#whitelist}

Liste des domaines désignés comme légitimes pour communiquer avec l’authentification Adobe Primetime.

## Jeton XSTS {#xsts-token}

Jeton de sécurité émis par Microsoft pour le développement de l&#39;application Xbox Console, utilisé dans l&#39;intégration de l&#39;authentification Xbox/Adobe Primetime.
