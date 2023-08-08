---
title: Modèles d’implémentation
description: Modèles d’implémentation
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Modèles d’implémentation {#imp-models}

## Stratégies côté serveur {#ss-policies}

Ce modèle utilisera CM comme point de décision de stratégie, déléguant ainsi la décision d’accès au service.

Puisque le client ne doit pas présumer des stratégies appliquées, l’implémentation doit vérifier la décision lors de l’initialisation de la session, ainsi que régulièrement, pendant la lecture à partir de la réponse de pulsation.
