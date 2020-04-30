---
seo-title: Codes d'erreur BEES
title: Codes d'erreur BEES
uuid: 7b2d0dd1-9a43-47e3-b932-a4eaf784ae7a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Codes d&#39;erreur BEES {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

En cas d&#39;erreur lors d&#39;une vérification des abeilles, une erreur `DRMErrorEvent` sera renvoyée au client. Vous pouvez analyser les propriétés de ce événement pour trouver des détails sur la nature de l’échec. Vous trouverez ci-dessous un sous-ensemble de codes d’erreur possibles.

| Erreur | Description |
|---|---|
| `3304:305` | Erreur générique d’autorisation de Primetime Cloud DRM tentant de gérer une demande d’authentification/d’autorisation. Généralement non associé à un problème d’abeilles. Si cette erreur est rencontrée de manière constante, vous devez envoyer un ticket d’incident à l’équipe DRM de Primetime Cloud avec les informations de diagnostic. |
| `3329:0` | Erreur spécifique à l&#39;application (provenant de l&#39;ordonnateur BEES). Si aucun code de sous-erreur n’a été renvoyé, le texte de l’erreur affiche les détails du problème. Par exemple, un problème s&#39;est produit lors de l&#39;analyse de la réponse, ou le serveur BEES était inatteignable. |
| `3329:<HTTP error code>` | Une réponse HTTP autre que 200 a été émise par le serveur BEES. Le code d’erreur HTTP est renvoyé au client dans le champ de code de sous-erreur. Cela peut indiquer un problème de configuration ou une panne du serveur BEES. |
| `3329:<x>` | Le serveur BEES A DÉSACTIVÉ la demande de licence. Le code de sous-erreur et le texte d’erreur sont spécifiés par le serveur BEES dans les propriétés `error` et propriétés de la réponse JSON `errorText` . Ce type de réponse ne doit pas être considéré comme une erreur, mais plutôt comme une réponse de refus régulière de votre serveur BEES. |