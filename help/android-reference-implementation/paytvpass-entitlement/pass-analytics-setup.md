---
description: Vous pouvez configurer l’implémentation des références pour utiliser le rapports Adobe Analytics.
seo-description: Vous pouvez configurer l’implémentation des références pour utiliser le rapports Adobe Analytics.
seo-title: Configuration d’Adobe Analytics Rapports
title: Configuration d’Adobe Analytics Rapports
uuid: bdf8bb7f-a0c8-48a2-a632-0b872687f3fe
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Configuration d’Adobe Analytics Rapports {#configure-adobe-analytics-reporting}

Vous pouvez configurer l’implémentation des références pour utiliser le rapports Adobe Analytics.

L’implémentation de référence est configurée pour envoyer les données du événement d’authentification Primetime à Adobe Analytics à l’aide de la bibliothèque mobile Adobe intégrée dans le SDK Primetime. Pour activer et utiliser les données de événement envoyées à partir de l’application, vous devez d’abord créer un compte Adobe Analytics. Une fois le compte créé :

1. Configurez l&#39;application avec les informations de votre compte ; et
1. Créez des règles de traitement pour personnaliser la manière dont les données du événement sont affichées dans vos rapports.

Le tableau ci-dessous présente les données envoyées à Adobe Analytics :

| Nom de l’action | `a.media.pass.event.MvpdSelection` | L’utilisateur a sélectionné un répartiteur de programmation vidéo à canaux multiples (MVPD) dans une boîte de dialogue de sélection. |
|---|---|---|
| Données contextuelles | `a.media.pass.MvpdId (String)` | La MVPD sélectionnée par l&#39;utilisateur |
|  | `a.media.pass.ClientType` | (Chaîne) Type de client : &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot; |
|  |  |  |
| Nom de l’action | `a.media.pass.event.AuthenticationDetection` | Processus d’authentification terminé |
| Données contextuelles | `a.media.pass.Successful` | (Boolean) Indique si la demande de jeton a réussi, true ou false |
|  | `a.media.pass.MvpdId` | (Chaîne) MVPD sélectionné par l’utilisateur |
|  | `a.media.pass.Guid` | (Chaîne) ID de suivi |
|  | `a.media.pass.Cached` | (booléen) Jeton déjà en cache, vrai ou faux |
|  | `a.media.pass.ClientType` | (Chaîne) Type de client : &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot; |
|  |  |  |
| Nom de l’action | `a.media.pass.event.AuthorizationDetection` | Processus d&#39;autorisation terminé |
| Données contextuelles | `a.media.pass.Successful` | (Boolean) Indique si la demande de jeton a réussi, true ou false |
|  | `a.media.pass.MvpdId` | (Chaîne) L&#39;utilisateur a sélectionné la MVPD |
|  | `a.media.pass.Guid` | (Chaîne) ID de suivi |
|  | `a.media.pass.Cached` | (booléen) Jeton déjà en cache, vrai ou faux |
|  | `a.media.pass.Error` | (Chaîne) Erreur si la tentative d&#39;autorisation a échoué |
|  | `a.media.pass.ErrorDetails` | (Chaîne) Détails d’erreur supplémentaires |
|  | `a.media.pass.ClientType` | (Chaîne) Type de client : &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; ou &quot;android&quot; |

1. Configurez l’application en vue de l’utiliser avec Adobe Marketing Cloud.

   Pour permettre l’envoi des données d’authentification Primetime à Adobe Analytics, un fichier [!DNL `ADBMobileConfig.json`] de configuration doit être ajouté à l’implémentation de référence au moment de la compilation. Notez qu’il s’agit exactement du même fichier de configuration utilisé par le SDK Primetime pour envoyer les données d’analyse vidéo à Marketing Cloud. Pour plus d’informations sur la configuration d’une application avec votre compte Adobe Analytics, consultez la documentation [d’](https://microsite.omniture.com/t2/help/en_US/reference/) Adobe Marketing Cloud.
1. Créez des règles de traitement.

   Les données du événement d’authentification Primetime envoyées par l’implémentation de référence n’apparaîtront pas automatiquement dans vos rapports d’analyse. Vous devez d’abord utiliser les données en créant des règles de traitement. Consultez la documentation d’ [Adobe Analytics sur la création de règles](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html)de traitement.
