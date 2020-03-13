---
seo-title: BEES Codes d’erreur
title: BEES Codes d’erreur
uuid: 7b2d0dd1-9a43-47e3-b932-a4eaf784ae7a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# BEES Codes d’erreur {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

En cas d’erreur lors d’une vérification d’AES, une erreur `DRMErrorEvent` sera renvoyée au client. Vous pouvez analyser ces propriétés  de pour trouver des détails sur la nature de l’échec. Un sous-ensemble de codes d’erreur possibles est répertorié ci-dessous.

| Erreur | Description |
|---|---|
| `3304:305` | Erreur générique d’autorisation de Primetime Cloud DRM tentant de traiter une demande d’authentification/d’autorisation. Généralement non associé à un problème BEES. Si cette erreur est rencontrée de manière constante, vous devez envoyer un ticket d’incident à l’équipe DRM de Primetime Cloud avec des informations de diagnostic. |
| `3329:0` | Erreur spécifique à l’application (provenant de l’autorité BEES). Si aucun code de sous-erreur n’a été renvoyé, le texte de l’erreur affiche les détails du problème. Par exemple, un problème est survenu lors de l’analyse de la réponse, ou le serveur BEES était . |
| `3329:<HTTP error code>` | Une réponse HTTP autre que 200 a été émise par le serveur BEES. Le code d’erreur HTTP est renvoyé au client dans le champ du code de sous-erreur. Cela peut indiquer un problème de configuration ou une panne du serveur BEES. |
| `3329:<x>` | LE serveur BEES A DÉSACTIVÉ la demande de licence. Le code de sous-erreur et le texte d’erreur sont spécifiés par le serveur BEES dans les propriétés `error` `errorText` et les propriétés de la réponse JSON. Ce type de réponse ne doit pas être considéré comme une erreur, mais plutôt comme une réponse de déni régulière de votre serveur BEES. |