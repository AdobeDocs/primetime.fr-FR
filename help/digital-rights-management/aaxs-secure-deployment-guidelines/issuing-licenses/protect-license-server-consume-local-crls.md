---
seo-title: Consommer des listes CRL générées localement
title: Consommer des listes CRL générées localement
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Consommer des listes CRL générées localement{#consume-locally-generated-crls}

Pour utiliser les  de révocation des certificats (CRL) générées localement et les de mise à jour des stratégies, utilisez les API Adobe Access pour vérifier la signature. Les API vérifient que le n’a pas été modifié et qu’il a été signé par le serveur de licence approprié.

* Appelez `RevocationList.verifySignature` pour vérifier la signature avant de fournir la liste de révocation à toute API.

   Pour plus d’informations, voir `RevocationListFactory` le Guide de référence *de l’API d’accès* Adobe.

* Appelez `PolicyUpdateList.verifySignature`à vérifier la signature avant de fournir le `PolicyUpdateList` à n’importe quelle API.

   Pour plus d’informations, voir `PolicyUpdateList` le Guide de référence *de l’API d’accès* Adobe.

