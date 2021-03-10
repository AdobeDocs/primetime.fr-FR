---
title: Consommer des listes CRL générées localement
description: Consommer des listes CRL générées localement
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Consommer des listes CRL générées localement{#consume-locally-generated-crls}

Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API d’accès aux Adobes pour vérifier la signature. Les API vérifient que les listes n’ont pas été modifiées et qu’elles ont été signées par le serveur de licence approprié.

* Appelez `RevocationList.verifySignature` pour vérifier la signature avant de fournir RevocationList à toute API.

   Pour plus d&#39;informations, voir `RevocationListFactory` dans le *Guide de référence de l&#39;API d&#39;accès aux Adobes*.

* Appelez `PolicyUpdateList.verifySignature`pour vérifier la signature avant de fournir `PolicyUpdateList` à toute API.

   Pour plus d&#39;informations, voir `PolicyUpdateList` dans le *Guide de référence de l&#39;API d&#39;accès aux Adobes*.

