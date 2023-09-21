---
description: Vous pouvez configurer l’implémentation de référence pour utiliser le reporting Adobe Analytics.
title: Configuration des rapports Adobe Analytics
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration des rapports Adobe Analytics {#configure-adobe-analytics-reporting}

Vous pouvez configurer l’implémentation de référence pour utiliser le reporting Adobe Analytics.

L’implémentation de référence est configurée pour envoyer des données d’événement d’authentification Primetime à Adobe Analytics à l’aide de la bibliothèque mobile Adobe intégrée dans le SDK Primetime. Pour activer et utiliser les données d’événement envoyées à partir de l’application, vous devez d’abord créer un compte Adobe Analytics. Une fois le compte créé :

1. configurer l’application avec les informations de votre compte ;
1. Créez des règles de traitement pour personnaliser l’affichage des données d’événement dans vos rapports.

Le tableau ci-dessous présente les données envoyées à Adobe Analytics :

| Nom de l’action | `a.media.pass.event.MvpdSelection` | L’utilisateur a sélectionné un répartiteur de programmation vidéo multicanal (MVPD) dans une boîte de dialogue de sélection. |
|---|---|---|
| Données contextuelles | `a.media.pass.MvpdId (String)` | MVPD sélectionné par l’utilisateur |
|  | `a.media.pass.ClientType` | (String) Le type de client est &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot;. |
|  | | |
| Nom de l’action | `a.media.pass.event.AuthenticationDetection` | Processus d’authentification terminé |
| Données contextuelles | `a.media.pass.Successful` | (Booléen) Indique si la requête de jeton a réussi, vrai ou faux. |
|  | `a.media.pass.MvpdId` | (chaîne) MVPD sélectionné par l’utilisateur |
|  | `a.media.pass.Guid` | (chaîne) Un ID de suivi |
|  | `a.media.pass.Cached` | (booléen) Jeton déjà en cache, vrai ou faux |
|  | `a.media.pass.ClientType` | (String) Le type de client est &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot;. |
|  | | |
| Nom de l’action | `a.media.pass.event.AuthorizationDetection` | Un workflow d’autorisation terminé |
| Données contextuelles | `a.media.pass.Successful` | (Booléen) Indique si la requête de jeton a réussi, vrai ou faux. |
|  | `a.media.pass.MvpdId` | (chaîne) L’utilisateur a sélectionné MVPD |
|  | `a.media.pass.Guid` | (chaîne) Un ID de suivi |
|  | `a.media.pass.Cached` | (booléen) Jeton déjà en cache, vrai ou faux |
|  | `a.media.pass.Error` | (Chaîne) Erreur si la tentative d’autorisation a échoué |
|  | `a.media.pass.ErrorDetails` | (Chaîne) Informations supplémentaires sur l’erreur |
|  | `a.media.pass.ClientType` | (String) Le type de client est &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot;. |

1. Configurez l’application à utiliser avec Adobe Marketing Cloud.

   Pour activer l’envoi de données d’authentification Primetime à Adobe Analytics, une [!DNL `ADBMobileConfig.json`] Le fichier de configuration doit être ajouté à la mise en oeuvre de référence au moment de la compilation. Notez qu’il s’agit exactement du même fichier de configuration utilisé par le SDK Primetime pour envoyer des données d’analyse vidéo au Marketing Cloud. Consultez la [Documentation Adobe Marketing Cloud](https://microsite.omniture.com/t2/help/en_US/reference/) pour plus d’informations sur la configuration d’une application avec votre compte Adobe Analytics.
1. Créez des règles de traitement.

   Les données d’événement d’authentification Primetime envoyées par l’implémentation de référence n’apparaîtront pas automatiquement dans vos rapports d’analyse. Vous devez d’abord utiliser les données en créant des règles de traitement. Consultez la [Documentation Adobe Analytics sur la création de règles de traitement](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html).
