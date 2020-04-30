---
seo-title: Consommer des listes CRL générées localement
title: Consommer des listes CRL générées localement
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: ''

---


# Consommer des listes CRL générées localement{#consume-locally-generated-crls}

Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API Adobe Access pour vérifier la signature. Les API vérifient que les listes n’ont pas été modifiées et qu’elles ont été signées par le serveur de licence approprié.

* Appelez `RevocationList.verifySignature` pour vérifier la signature avant de fournir RevocationList à toute API.

   Pour plus d’informations, voir `RevocationListFactory` le Guide de référence *de l’API* Adobe Access.

* Appelez `PolicyUpdateList.verifySignature`pour vérifier la signature avant de fournir la `PolicyUpdateList` aux API.

   Pour plus d’informations, voir `PolicyUpdateList` le Guide de référence *de l’API* Adobe Access.

