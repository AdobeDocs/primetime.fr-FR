---
title: Utilisation de listes CRL générées localement
description: Utilisation de listes CRL générées localement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Utilisation de listes CRL générées localement{#consume-locally-generated-crls}

Pour utiliser des listes de révocation des certificats générées localement et des listes de mise à jour de stratégie, utilisez les API Adobe Access pour vérifier la signature. Les API vérifient que les listes n’ont pas été modifiées et qu’elles ont été signées par le bon serveur de licences.

* Appeler `RevocationList.verifySignature` pour vérifier la signature avant de fournir RevocationList à toute API.

  Pour plus d’informations, voir `RevocationListFactory` dans le *Référence de l’API Adobe Access*.

* Appeler `PolicyUpdateList.verifySignature`pour vérifier la signature avant de fournir l’événement `PolicyUpdateList` à toute API.

  Pour plus d’informations, voir `PolicyUpdateList` dans le *Référence de l’API Adobe Access*.
