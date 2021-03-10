---
title: Création d’un gestionnaire DRMErrorEvent
description: Création d’un gestionnaire DRMErrorEvent
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Création d’un gestionnaire DRMErrorEvent{#create-a-drmerrorevent-handler}

Créez un gestionnaire de événements pour traiter les événements d’erreur envoyés à partir de Primetime lorsqu’il rencontre une erreur lors de la tentative de lecture d’un contenu protégé.

Normalement, lorsqu’une application rencontre une erreur, elle effectue un nombre indéfini de tâches de nettoyage. Il informe ensuite l’utilisateur de l’erreur et fournit des options pour résoudre le problème.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

