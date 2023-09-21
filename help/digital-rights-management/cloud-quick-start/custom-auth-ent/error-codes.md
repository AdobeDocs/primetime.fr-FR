---
title: Codes d’erreur BEES
description: Codes d’erreur BEES
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Codes d’erreur BEES {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

Si une erreur se produit lors d’une vérification BEES, une `DRMErrorEvent` est renvoyée au client. Vous pouvez analyser les propriétés de cet événement pour trouver des détails sur la nature de l’échec. Vous trouverez ci-dessous un sous-ensemble de codes d’erreur possibles.

| Erreur | Description |
|---|---|
| `3304:305` | Erreur générique d’autorisation de Primetime Cloud DRM tentant de gérer une demande d’authentification/d’autorisation. En règle générale, non associé à un problème d’abeilles. Si cette erreur est rencontrée de manière cohérente, vous devez envoyer un ticket de dépannage à l’équipe DRM de Primetime Cloud avec des informations de diagnostic. |
| `3329:0` | Erreur spécifique à l’application (de l’agent d’autorisation BEES). Si aucun code de sous-erreur n’a été renvoyé, le texte d’erreur affiche les détails du problème. Par exemple, un problème est survenu lors de l’analyse de la réponse ou le serveur BEES n’a pas été accessible. |
| `3329:<HTTP error code>` | Une réponse HTTP autre que 200 a été émise par le serveur BEES. Le code d’erreur HTTP est renvoyé au client dans le champ code de sous-erreur . Cela peut indiquer un problème de configuration ou une panne du serveur BEES. |
| `3329:<x>` | Le serveur BEES A DÉSACTIVÉ la demande de licence. Le code de sous-erreur et le texte d’erreur sont spécifiés par le serveur BEES dans le fichier de réponse JSON. `error` et `errorText` propriétés. Ce type de réponse ne doit pas être considéré comme une erreur, mais plutôt comme une réponse de refus régulière de votre serveur BEES. |
